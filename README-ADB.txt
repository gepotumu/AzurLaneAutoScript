adb kill-server
adb connect host.docker.internal:5555
adb devices
# 先连接到模拟器
adb -s emulator-5554 tcpip 5555

# DOCKER
docker run -it \
  --name azurlaneautoscript \
  -e TZ=Asia/Shanghai \
  -p 127.0.0.1:22267:22267 \
  -v /Users/finderz/Documents/AzurLaneAutoScript:/app/AzurLaneAutoScript:rw \
  -v /Users/finderz/.android/adbkey:/root/.android/adbkey:ro \
  -v /Users/finderz/.android/adbkey.pub:/root/.android/adbkey.pub:ro \
  --log-opt max-size=20m \
  --log-opt max-file=5 \
  -d \
  binss/azurlaneautoscript:arm64

# requirements
docker exec -it azurlaneautoscript /app/pyroot/bin/pip install onepush==1.4.0 pydantic uiautomator2cache

#Config
模拟器 Serial: host.docker.internal:5555
模拟器截图方案: ADB_nc
模拟器控制方案: MaaTouch

# Documents
https://www.binss.me/blog/run-azurlaneautoscript-on-arm64/