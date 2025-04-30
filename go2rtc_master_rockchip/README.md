# Go2RTC Master Rockchip

这是一个为 Rockchip 设备优化的 Go2RTC Home Assistant 插件，支持硬件转码功能。

## 功能特点

- 支持 Rockchip 硬件转码（使用 MPP 硬件加速）
- WebRTC 流媒体支持
- RTSP 流媒体支持
- RTMP 流媒体支持
- 与 Home Assistant 深度集成

## 系统要求

- Home Assistant 运行在 Rockchip 设备上（如 RK3566、RK3588 等）
- 系统已安装 MPP（Media Process Platform）驱动

## 安装

1. 在 Home Assistant 中添加此仓库
2. 在插件商店中找到 "Go2RTC Master Rockchip"
3. 点击安装

## 配置

插件安装后，您需要在 `/config/go2rtc.yaml` 中配置您的流媒体源。配置文件示例：

```yaml
api:
  origin: "*"
  token: ""

webrtc:
  candidates: []

rtsp:
  username: ""
  password: ""

rtmp:
  port: 1935

hass:
  token: "${SUPERVISOR_TOKEN}"

# Rockchip 硬件加速配置
ffmpeg:
  hwaccel: rkmpp
  hwaccel_output: rkmpp
```

## 使用说明

1. 安装完成后，插件会自动启动
2. 访问 `http://your-ha-ip:1984` 查看 Web 界面
3. 在配置文件中添加您的流媒体源
4. 重启插件使配置生效

## 硬件加速说明

本插件使用 Rockchip MPP 进行硬件加速，支持以下功能：
- H.264/H.265 硬件解码
- H.264/H.265 硬件编码
- 硬件缩放和格式转换

## 故障排除

如果遇到硬件加速问题：
1. 确认系统已正确安装 MPP 驱动
2. 检查 `/dev/mpp_service` 设备是否存在
3. 查看日志中是否有 MPP 相关错误

## 支持

如有问题，请访问 [GitHub Issues](https://github.com/AlexxIT/go2rtc/issues) 