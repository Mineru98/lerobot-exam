# lerobot-exam

## TODO

- [x] usb 포트 확인 및 ID 부여
- [ ] calibrate
- [x] Camera Connect
- [ ] Teleoperate
- [ ] OpenCVCameraConfig : index 확인

## usb 포트 확인 및 ID 부여

### 12V (팔로워)

```bash
# 실행
python lerobot/find_port.py

sudo chmod 666 /dev/tty.usbmodem5A7A0186761

python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 1

python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 2

python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 3

python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 4

python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 5

python lerobot/scripts/configure_motor.py \
  --port /dev/tty.usbmodem5A7A0186761 \
  --brand feetech \
  --model sts3215 \
  --baudrate 1000000 \
  --ID 6

python -m lerobot.setup_motors \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5A7A0186761

python -m lerobot.calibrate \
    --robot.type=so101_follower \
    --robot.port=/dev/tty.usbmodem5A7A0186761 \
    --robot.id=usefullabs_follower_arm
```

### 5V (리더)

```bash
sudo chmod 666 /dev/tty.usbmodem5A7A0186941

python -m lerobot.setup_motors \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5A7A0186941

python -m lerobot.calibrate \
    --teleop.type=so101_leader \
    --teleop.port=/dev/tty.usbmodem5A7A0186941 \
    --teleop.id=usefullabs_leader_arm
```

## calibrate

### 12V (팔로워, 흰색)

```bash
python lerobot/scripts/control_robot.py \
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
python lerobot/scripts/control_robot.py \
  --robot.type=so101 \
  --robot.cameras='{}' \
  --control.type=teleoperate
```

```
python lerobot/scripts/eval.py --pretrained_policy.path=lerobot/smolvla_base
```