adb kill-server
adb connect host.docker.internal:5555
adb devices
# 先连接到模拟器
adb -s emulator-5554 tcpip 5555