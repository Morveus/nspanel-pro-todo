# nspanel-pro-todo
Personal checklist to follow when deploying a new NSPanelPro

NSPanelProTools: https://github.com/seaky/nspanel_pro_tools_apk

# Go dev
In the ewelink app, go to settings, tap 10 times on the system version and enable `Developer Mode`

# ADB
```
adb connect <IP>
adb install -r ultra-small-launcher.apk
adb install -r nspanel-pro-tools-2.2.2-release.apk
adb install -r homeassistant-app-minimal-release.apk
adb install -r com.android.webview_108.0.5359.128-535912803.apk
```

# Go home
Simulate a press on the Android Home Button
```
adb shell input keyevent 3
```
and select the new launcher.

# Android Settings
In `Settings` > `Sound` > `Other sounds and vibration`, disable everything

# NSPanel Settings
## Display Tab
- Open the NSPanelTools from Ultra Small Launcher
- Click "Active" in the top-right corner ✅
- Wake on Wave ✅
- Wake from Screen savers ✅
- Display Sleep `15 seconds`
- Display Sleep mode `Screen dim`

## Tools Tab
- Launch App After Reboot: `HomeAssistant`
- Wait for WiFi :check
- Watchdog ✅
- NavigationBar ❌
- NavigationBar on swipe up ❌
- NotificationBar on swipe down ❌
- Home on gesture ❌

## Integration Tab
- Enabled MQTT, enter MQTT server info
- Update MQTT Client Id
- Enable HA Integration ✅
- Topic prefix: `homeassistant`

## Settings Tab
- Resume on boot ✅
- Scheduled reboot when applicable ✅ (⚠ bedrooms)


# Disable all useless services and packages
```
adb shell
su
pm disable com.eWeLinkControlPanel
pm disable com.eWeLinkNSPro.dev
pm disable com.rockchip.devicetest
pm disable android.rockchip.update.service
pm disable com.android.gl2jni
pm disable com.smatek.test
pm disable android.rk.RockVideoPlayer
pm disable acr.browser.barebones
pm disable org.chromium.webview_shell
pm disable com.android.music
pm disable com.android.nfc
pm disable com.DeviceTest
pm disable com.cghs.stresstest
```
