# Maestro 操作规则

## 规则 1：优先使用 inspect screen

使用 Maestro MCP 的 `inspect_screen` 获取界面元素信息，而不是截图。

inspect screen 提供准确的元素 bounds 和层级结构，比截图更可靠。

## 规则 2：键盘弹起后必须重新获取坐标

点击输入框后键盘弹起，界面实际位置会发生变化。

**必须**用 `inspect_screen` 重新获取准确的 bounds 后再计算点击坐标，不要使用键盘弹起前的坐标。

## 规则 3：Maestro 不支持方向键

`pressKey` 只支持：`enter`, `home`, `lock`, `backspace`, `volume up`, `volume down`, `back`, `power`, `tab`

**不支持**左/右/上/下方向键。需要方向键时，使用 adb：
```bash
adb shell input keyevent KEYCODE_DPAD_LEFT
adb shell input keyevent KEYCODE_DPAD_RIGHT
adb shell input keyevent KEYCODE_DPAD_UP
adb shell input keyevent KEYCODE_DPAD_DOWN
```

## 规则 4：先验证每一步的状态，再进行下一步

不要猜测操作结果然后盲目继续。每一步操作后，用 `inspect_screen` 确认当前界面状态，确认符合预期后再执行下一步。

## 规则 5：反复失败时立即请教用户
