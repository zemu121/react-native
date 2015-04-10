# IOS 活动指示器

## Props  [Edit on GitHub]( https://github.com/facebook/react-native/blob/master/Libraries/Components/ActivityIndicatorIOS/ActivityIndicatorIOS.ios.js)

**animating** bool 型


显示指示器(true，默认的)还是隐藏它(false)。

**color** 字符串型

Spinner 的前景颜色(默认为灰色)。

**size** 枚举型(“小”，“大”)

指示器的大小。小的高度为 20，大的高度为 36。

## 例子      [Edit on GitHub]( https://github.com/facebook/react-native/blob/master/Examples/UIExplorer/ActivityIndicatorIOSExample.js)

```
'use strict';
var React = require('react-native');
var {
  ActivityIndicatorIOS,
  StyleSheet,
  View,
} = React;
var TimerMixin = require('react-timer-mixin');
var ToggleAnimatingActivityIndicator = React.createClass({
  mixins: [TimerMixin],
  getInitialState: function() {
    return {
      animating: true,
    };
  },
  setToggleTimeout: function() {
    this.setTimeout(
      () => {
        this.setState({animating: !this.state.animating});
        this.setToggleTimeout();
      },
      1200
    );
  },
  componentDidMount: function() {
    this.setToggleTimeout();
  },
  render: function() {
    return (
      <ActivityIndicatorIOS
        animating={this.state.animating}
        style={[styles.centering, {height: 80}]}
        size="large"
      />
    );
  }
});
exports.framework = 'React';
exports.title = '<ActivityIndicatorIOS>';
exports.description = 'Animated loading indicators.';
exports.examples = [
  {
    title: 'Default (small, white)',
    render: function() {
      return (
        <ActivityIndicatorIOS
          style={[styles.centering, styles.gray, {height: 40}]}
          color="white"
          />
      );
    }
  },
  {
    title: 'Gray',
    render: function() {
      return (
        <View>
          <ActivityIndicatorIOS
            style={[styles.centering, {height: 40}]}
          />
          <ActivityIndicatorIOS
            style={[styles.centering, {backgroundColor: '#eeeeee', height: 40}]}
          />
        </View>
      );
    }
  },
  {
    title: 'Custom colors',
    render: function() {
      return (
        <View style={styles.horizontal}>
          <ActivityIndicatorIOS color="#0000ff" />
          <ActivityIndicatorIOS color="#aa00aa" />
          <ActivityIndicatorIOS color="#aa3300" />
          <ActivityIndicatorIOS color="#00aa00" />
        </View>
      );
    }
  },
  {
    title: 'Large',
    render: function() {
      return (
        <ActivityIndicatorIOS
          style={[styles.centering, styles.gray, {height: 80}]}
          color="white"
          size="large"
        />
      );
    }
  },
  {
    title: 'Large, custom colors',
    render: function() {
      return (
        <View style={styles.horizontal}>
          <ActivityIndicatorIOS
            size="large"
            color="#0000ff"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#aa00aa"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#aa3300"
          />
          <ActivityIndicatorIOS
            size="large"
            color="#00aa00"
          />
        </View>
      );
    }
  },
  {
    title: 'Start/stop',
    render: function(): ReactElement {
      return <ToggleAnimatingActivityIndicator />;
    }
  },
];
var styles = StyleSheet.create({
  centering: {
    alignItems: 'center',
    justifyContent: 'center',
  },
  gray: {
    backgroundColor: '#cccccc',
  },
  horizontal: {
    flexDirection: 'row',
    justifyContent: 'space-around',
  },
});
```

[下一页]( http://facebook.github.io/react-native/docs/datepickerios.html#content)
