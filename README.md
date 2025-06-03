# lerobot-exam

## TODO

- [x] usb 포트 확인 및 ID 부여
- [ ] calibrate
- [x] Camera Connect
- [ ] Teleoperate

## usb 포트 확인 및 ID 부여

### 12V (팔로워)

```bash
# 실행
python scripts/find_motors_bus_port.py

sudo chmod 666 /dev/tty.usbmodem5A7A0186941

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186941 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 1

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186941 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 2

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186941 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 3

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186941 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 4

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186941 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 5

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186941 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 6
```

### 5V (리더)

```bash
sudo chmod 666 /dev/tty.usbmodem5A7A0186761

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 1

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 2

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 3

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 4

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 5

python scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 6
```

## calibrate

### 12V (팔로워, 흰색)

```bash
python scripts/control_robot.py \
  --robot.type=so101 \
  --robot.cameras='{}' \
  --control.type=calibrate \
  --control.arms='["main_follower"]'
```

### 5V (리더, 검은색)

```bash
python lerobot/scripts/control_robot.py \
  --robot.type=so101 \
  --robot.cameras='{}' \
  --control.type=calibrate \
  --control.arms='["main_leader"]'
```

## 카메라 연결 

```bash
python lerobot/common/robot_devices/cameras/opencv.py \
    --images-dir outputs/images_from_opencv_cameras
```

## Teleoperate

```bash
python scripts/control_robot.py \
  --robot.type=so101 \
  --robot.cameras='{}' \
  --control.type=teleoperate
```