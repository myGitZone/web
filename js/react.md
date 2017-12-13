# react开发规范
## 命名
* 文件夹命名
    * 由名词组成,组件的根目录使用帕斯卡命名法，如：ReservationCard![image](../image/folder.png)。
    * 其他文件夹使用单个有意义名词命名，使用小写字母
* 组件命名（*.jsx）
  * 使用 jsx 作为 React 组件的扩展名
  * 组件引用采用帕斯卡命名法，其实例采用驼峰式命名法
    ```jsx
    // bad
    const reservationCard = require('./ReservationCard');

    // good
    const ReservationCard = require('./ReservationCard');

    // bad
    const ReservationItem = <ReservationCard />;

    // good
    const reservationItem = <ReservationCard />;
    ```
* 类命名
  * 使用es6语法
    ```jsx
      class Demo extends React.Component{

      }
    ```
* 函数命名
    * 公有函数使用小驼峰式命名，如getName() {}
    * 如果是私有的则在函数名前加“_”,如 _getName(){}
# 使用
  * 书写顺序
    * optional static methods
    * constructor
    * getChildContext(一般情况不会使用)
    * componentWillMount
    * componentDidMount
    * componentWillReceiveProps
    * shouldComponentUpdate
    * componentWillUpdate
    * componentDidUpdate
    * componentWillUnmount
    * clickHandlers or eventHandlers like onClickSubmit() or onChangeDescription()
    * render
    ```jsx
      class Demo extends React.Component{
        static demo = {}
        constructor(props) {
          super(props)
        }
        // 将要挂载到视图
        componentWillMount() {
          
        }
        // 已经挂载到视图
        componentDidMount() {

        }
        // props发生变化
        componentWillReceiveProps() {

        }
        // 是否执行更新（调用render函数），return true则刷新，return false则不进行刷新
        shouldComponentUpdate() {

        }
        // 将要执行更新
        componentWillUpdate() {
          
        }
        // 完成更新
        componentDidUpdate() {
          
        }
        // 组件卸载完成 
        componentWillUnmount() {

        }
        // 响应事件
        handeles() {

        }
        // 私有方法
        _privateFunc() {

        }
        // render函数
        render() {

        }
      }
    ```
  * props定义
    * props使用小驼峰命名
      ```jsx
        // bad
        <Foo
          UserName="hello"
          phone_number={12345678}
        />

        // good
        <Foo
          userName="hello"
          phoneNumber={12345678}
        />
      ```
    * 总是为所有非必需的道具定义明确的defaultProps。
      ```jsx
        // bad
        function SFC({ foo, bar, children }) {
          return <div>{foo}{bar}{children}</div>;
        }
        SFC.propTypes = {
          foo: PropTypes.number.isRequired,
          bar: PropTypes.string,
          children: PropTypes.node,
        };

        // good
        function SFC({ foo, bar, children }) {
          return <div>{foo}{bar}{children}</div>;
        }
        SFC.propTypes = {
          foo: PropTypes.number.isRequired,
          bar: PropTypes.string,
          children: PropTypes.node,
        };
        SFC.defaultProps = {
          bar: '',
          children: null,
        };

        // good
        function SFC({ foo, bar, children }) {
          return <div>{foo}{bar}{children}</div>;
        }
        SFC.propTypes = {
          foo: PropTypes.number.isRequired,
          bar: PropTypes.string,
          children: PropTypes.node,
        };
        SFC.defaultProps = {
          bar: '',
          children: null,
        };

        // good
        class SFC extends React.Component {
          static propTypes = {
            foo: PropTypes.number.isRequired,
            bar: PropTypes.string,
            children: PropTypes.node,
          }
          static defaultProps = {
            bar: '',
            children: null,
          }
          constructor(props) {
            super(props);
            this.onClickDiv = this.onClickDiv.bind(this);
          }
        }
      ```
