# lerobot-exam

## TODO

- [x] usb 포트 확인 및 ID 부여
- [ ] calibrate
- [x] Camera Connect
- [ ] Teleoperate
- [ ] OpenCVCameraConfig : index 확인


## 디바이스 확인

```
python lerobot/scripts/find_motors_bus_port.py
```

## usb 포트 확인

```bash
# 5V (리더) 왼쪽
sudo chmod 666 /dev/tty.usbmodem5A7A0186941

# 12V (팔로워) 오른쪽
sudo chmod 666 /dev/tty.usbmodem5A7A0186761
```

## ID 부여

```bash
# 리더 왼쪽
python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186941 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 6

# 팔로워 오른쪽
python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 1
```

## 캘리브레이션

```bash
python lerobot/scripts/control_robot.py \
  --robot.type=so101 \
  --control.type=calibrate
```

## Teleoperate

```bash
python lerobot/scripts/control_robot.py \
  --robot.type=so101 \
  --robot.cameras='{}' \
  --control.type=teleoperate
```


```
python lerobot/scripts/eval.py --pretrained_policy.path=lerobot/smolvla_base
```

