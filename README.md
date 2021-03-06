## Screen Capture

### 支持输入密码，兼容了 iOS 和 Android

|![android](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/react-native-sms-verifycode-android.gif)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/react-native-sms-verifycode-ios.gif)|![Password](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/react-native-sms-verifycode-password.gif)|
|:-:|:-:|:-:|
| on Android | on iOS | use Password |

在线Demo查看地址 [Expo](https://snack.expo.io/@shixiaoquan/-react-native-sms-verifycode-example)

## Installation

```bash
$ npm install react-native-sms-verifycode --save
```

## Usage

### Basic Usage

设置输入完成时的回调函数，即可获取用户输入的内容

```javascript
import SMSVerifyCode from 'react-native-sms-verifycode'
...
<SMSVerifyCode
  ref={ref => (this.verifycode = ref)}
  onInputCompleted={this.onInputCompleted}
/>

onInputCompleted = (text) => {
	Alert.alert(
	  text,
	  '本次输入的验证码',
	  [
	  	{
	      text: '确定',
	    },
	  ]
	)
}

reset = () => {
	this.verifycode.reset()
	this.setState({codeText: ''})
}
...        
```

|![android](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/normal-android.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/normal-ios.png)|![all](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/normal-all.gif)|
|:-:|:-:|:-:|

### Advanced Usage

#### 设置验证码的个数

```javascript
import SMSVerifyCode from 'react-native-sms-verifycode'
...
<SMSVerifyCode
  verifyCodeLength={4} // 根据需要设置任意数，类型必须时number
/>
```

|![android](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-number-4.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-number-5.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-number-6.png)|
|:-:|:-:|:-:|

#### 设置Container样式

```javascript
import SMSVerifyCode from 'react-native-sms-verifycode'
...
<SMSVerifyCode
  verifyCodeLength={5}
  containerPaddingVertical={10}
  containerPaddingHorizontal={50}
  containerBackgroundColor={'#8DC647'}
/>
...        
```

|![android](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-container-3.png)|![android](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-container-1.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-container-2.png)|
|:-:|:-:|:-:|

#### 设置文本框的样式

```javascript
import SMSVerifyCode from 'react-native-sms-verifycode'
...
<SMSVerifyCode
  verifyCodeLength={5}
  containerPaddingVertical={10}
  containerPaddingHorizontal={50}
  containerBackgroundColor={'#8DC647'}
  codeBorderColor={'#000000'}
  codeFocusedBorderColor={'#0000FF'}
  codeBorderWidth={3}
  // codeBorderRadius={26}
/>
...        
```

|![android](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-border-1.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-border-3.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-border-2.png)|
|:-:|:-:|:-:|

#### 设置文本的样式

```javascript
import SMSVerifyCode from 'react-native-sms-verifycode'
...
<SMSVerifyCode
  verifyCodeLength={5}
  codeFontSize={26}
  // codeFontColor={'#89C047'}
/>
...        
```

|![android](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-textstyle-1.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-textstyle-2.png)|![iOS](https://raw.githubusercontent.com/shixiaoquan/react-native-sms-verifycode/master/screencaptures/change-textstyle-3.png)|
|:-:|:-:|:-:|

## **Properties**

| Prop | PropType | Default Value |isRequired| Description |
|:-:|:-:|:-:|:-:|:-:|
| verifyCodeLength | number | 6 | NO | 验证码的个数 |
| containerPaddingVertical | number | 0 | NO | 外层容器的paddingVertical |
| containerPaddingHorizontal | number | 根据验证码个数自动计算 | NO | 外层容器的paddingHorizontal |
| containerBackgroundColor | string | #FDFFFD | NO | 外层容器的backgroundColor |
| codeBorderColor | string | grey | NO | 文本框的颜色 |
| codeFocusedBorderColor | string | #1192F6 | NO | 当前获得焦点的文本框的颜色 |
| codeViewWidth | number | 根据验证码个数自动计算 | NO | 文本框的宽度 |
| codeBorderWidth | number | 1 | NO | 文本框的粗细 |
| codeBorderRadius | number | 5 | NO | 文本框的圆角大小 |
| codeFontSize | number | default | NO | 文本的大小 |
| codeFontColor | string | #222222 | NO | 文本的颜色 |
| secureTextEntry | boolean | false | NO | 默认为false，需要设置为true时，只要secureTextEntry即可，不需要secureTextEntry={true} |

## **APIs**

| Name | isRequired | Description |
|:-:|:-:|:-:|
| onInputCompleted | NO | 输入完成时，回调的方法 |
| reset | NO | 清空输入的内容，并将焦点设置在第一个输入框，**使用ref调用** |
| blur | NO | 隐藏键盘，**使用ref调用** |
| focus | NO | 显示键盘，**使用ref调用** |



