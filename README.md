# Petoi Bittle

A Repository for custom code related to controlling the [Petoi Bittle Robot Dog](https://www.petoi.com/). What follows is an API reference for Python commands to control the dog.

## Setup

### Installing `pySerial`

Before you can send commands to the Petoi Bittle Robot Dog, you need to install the `pySerial` library. `pySerial` allows Python to communicate with serial devices, like the Petoi Bittle Robot Dog.

To install `pySerial`, open your command prompt or terminal and run:

```sh
pip install pyserial
```

For more information about `pip` and how to install it, refer to the official [pip documentation](https://pip.pypa.io/en/stable/).

### Establishing a Serial Connection

To communicate with the robot, you need to establish a serial connection. The following Python code can be used to automatically connect to the robot:

```python
import serial
import serial.tools.list_ports
import time

def autoConnect():
    ports = list(serial.tools.list_ports.comports())
    for p in ports:
        if "Petoi" in p.description:
            ser = serial.Serial(p.device, 115200)
            print("Connected to", p.device)
            return ser
    return None

ser = autoConnect()
if ser is None:
    print("No Petoi device found. Please check your connection.")
```

## Functions

Below is a detailed explanation of each function available in the API, along with examples of how to use them.

### `printH(head, value)`

This function prints debug information. It takes two parameters: `head` and `value`.

#### Example:

```python
printH("Debug Info:", "Connection successful")
```

### `deacGyro()`

This function deactivates the gyroscope (a device that measures orientation) of the robot.

#### Example:

```python
deacGyro()
```

### `getAngleList()`

This function returns the current angle list of all joints of the robot.

#### Example:

```python
angles = getAngleList()
print("Current Angles:", angles)
```

### `getCurAng(index)`

This function returns the current angle value of a specific joint.

#### Example:

```python
current_angle = getCurAng(1)
print("Current Angle of Joint 1:", current_angle)
```

### `absValList(num1, num2)`

This function creates a list of absolute values.

#### Example:

```python
abs_values = absValList(30, 60)
print("Absolute Values List:", abs_values)
```

### `relativeValList(index, symbol, angle)`

This function rotates an angle from a relative value to an absolute value and creates an offset value list.

#### Example:

```python
relative_values = relativeValList(1, '+', 15)
print("Relative Values List:", relative_values)
```

### `rotateJoints(token, var, delayTime)`

This function rotates the joints either sequentially or simultaneously.

#### Example:

```python
rotateJoints('m', [1, 30, 2, -30], 1000)
```

### `play(token, var, delayTime)`

This function plays tones.

#### Example:

```python
play('B', [12, 8, 16, 8], 500)
```

### `encode(in_str, encoding='utf-8')`

This function encodes a string to bytes.

#### Example:

```python
encoded_string = encode("Hello, Robot!")
print("Encoded String:", encoded_string)
```

### `printSkillFileName()`

This function prints the available skill file names.

#### Example:

```python
printSkillFileName()
```

### `openPort(port)`

This function opens the specified serial port.

#### Example:

```python
openPort('COM3')
```

### `autoConnect()`

This function automatically connects to the robot's serial port.

#### Example:

```python
ser = autoConnect()
if ser:
    print("Connected to the robot!")
else:
    print("No robot found.")
```

### `sendSkillStr(skillStr, delayTime)`

This function sends a short skill string to the robot.

#### Example:

```python
sendSkillStr(ser, 'ksit', 1000)
```

### `loadSkill(fileName, delayTime)`

This function loads and sends a skill from a file.

#### Example:

```python
loadSkill('standUp.md', 1000)
```

### `sendCmdStr(cmdStr, delayTime)`

This function sends a command string to the robot.

#### Example:

```python
sendCmdStr('m0 30', 1000)
```

### `sendLongCmd(token, var, delayTime)`

This function sends a long command to the robot.

#### Example:

```python
sendLongCmd('c', [0, 1, 2, 3, 4, 5], 1000)
```

### `readAnalogValue(pin)`

This function reads the analog value of a specified pin.

#### Example:

```python
analog_value = readAnalogValue(2)
print("Analog Value:", analog_value)
```

### `readDigitalValue(pin)`

This function reads the digital value of a specified pin.

#### Example:

```python
digital_value = readDigitalValue(3)
print("Digital Value:", digital_value)
```

### `writeAnalogValue(pin, val)`

This function sets the analog value of a specified pin.

#### Example:

```python
writeAnalogValue(2, 128)
```

### `writeDigitalValue(pin, val)`

This function sets the digital value of a specified pin.

#### Example:

```python
writeDigitalValue(3, 1)
```

### `closePort()`

This function closes the serial port.

#### Example:

```python
closePort()
```

## Sending Skills

Each skill is activated by sending a specific command string. Here is a list of skills and how to send them using Python.

### Built-in Skills and How to Send Them

See below.

#### Posture Skills

1. **Stand Up Neutral** (`balance`)

   ```python
   sendSkillStr(ser, 'kbalance')
   ```

2. **Butt Up** (`buttUp`)

   ```python
   sendSkillStr(ser, 'kbuttUp')
   ```

3. **Calibration Pose** (`calib`)

   ```python
   sendSkillStr(ser, 'kcalib')
   ```

4. **Dropped by Back Legs** (`dropped`)

   ```python
   sendSkillStr(ser, 'kdropped')
   ```

5. **Lifted by Neck** (`lifted`)

   ```python
   sendSkillStr(ser, 'klifted')
   ```

6. **Landing Pose** (`lnd`)

   ```python
   sendSkillStr(ser, 'klnd')
   ```

7. **Rest** (`rest`)

   ```python
   sendSkillStr(ser, 'krest')
   ```

8. **Sit** (`sit`)

   ```python
   sendSkillStr(ser, 'ksit')
   ```

9. **Stretch** (`str`)

   ```python
   sendSkillStr(ser, 'kstr')
   ```

10. **Stand Up Neutral (= balance)** (`up`)

    ```python
    sendSkillStr(ser, 'kup')
    ```

11. **All Joints at 0 Degrees** (`zero`)

    ```python
    sendSkillStr(ser, 'kzero')
    ```

#### Gait Skills

1. **Bound Forward** (`bdF`)

   ```python
   sendSkillStr(ser, 'kbdF')
   ```

2. **Backward** (`bk`)

   ```python
   sendSkillStr(ser, 'kbk')
   ```

3. **Backward Left** (`bkL`)

   ```python
   sendSkillStr(ser, 'kbkL')
   ```

4. **Crawl Forward** (`crF`)

   ```python
   sendSkillStr(ser, 'kcrF')
   ```

5. **Crawl Left** (`crL`)

   ```python
   sendSkillStr(ser, 'kcrL')
   ```

6. **Gap Forward** (`gpF`)

   ```python
   sendSkillStr(ser, 'kgpF')
   ```

7. **Gap Left** (`gpL`)

   ```python
   sendSkillStr(ser, 'kgpL')
   ```

8. **Halloween Gait** (`hlw`)

   ```python
   sendSkillStr(ser, 'khlw')
   ```

9. **Jump Forward** (`jpF`)

   ```python
   sendSkillStr(ser, 'kjpF')
   ```

10. **Push Forward** (`phF`)

    ```python
    sendSkillStr(ser, 'kphF')
    ```

11. **Push Left** (`phL`)

    ```python
    sendSkillStr(ser, 'kphL')
    ```

12. **Trot Forward** (`trF`)

    ```python
    sendSkillStr(ser, 'ktrF')
    ```

13. **Trot Left** (`trL`)

    ```python
    sendSkillStr(ser, 'ktrL')
    ```

14. **Step at Origin** (`vtF`)

    ```python
    sendSkillStr(ser, 'kvtF')
    ```

15. **Spin Left** (`vtL`)

    ```python
    sendSkillStr(ser, 'kvtL')
    ```

16. **Walk Forward** (`wkF`)

    ```python
    sendSkillStr(ser, 'kwkF')
    ```

17. **Walk Left** (`wkL`)

    ```python
    sendSkillStr(ser, 'kwkL')
    ```

#### Behavior Skills

1. **Angry** (`ang`)

   ```python
   sendSkillStr(ser, 'kang')
   ```

2. **Backflip** (`bf`)

   ```python
   sendSkillStr(ser, 'kbf')
   ```

3. **Boxing** (`bx`)

   ```python
   sendSkillStr(ser, 'kbx')
   ```

4. **Cheers** (`chr`)

   ```python
   sendSkillStr(ser, 'kchr')
   ```

5. **Check** (`ck`)

   ```python
   sendSkillStr(ser, 'kck')
   ```

6. **Come Here** (`cmh`)

   ```python
   sendSkillStr(ser, 'kcmh')
   ```

7. **Dig** (`dg`)

   ```python
   sendSkillStr(ser, 'kdg')
   ```

8. **Front Flip** (`ff`)

   ```python
   sendSkillStr(ser, 'kff')
   ```

9. **High Five** (`fiv`)

   ```python
   sendSkillStr(ser, 'kfiv')
   ```

10. **Good Boy** (`gdb`)

    ```python
    sendSkillStr(ser, 'kgdb')
    ```

11. **Handstand** (`hds`)

    ```python
    sendSkillStr(ser, 'khds')
    ```

12. **Hug** (`hg`)

    ```python
    sendSkillStr(ser, 'khg')
    ```

13. **Hi** (`hi`)

    ```python
    sendSkillStr(ser, 'khi')
    ```

14. **Hand Shake** (`hsk`)

    ```python
    sendSkillStr(ser, 'khsk')
    ```

15. **Hands Up** (`hu`)

    ```python
    sendSkillStr(ser, 'khu')
    ```

16. **Jump** (`jmp`)

    ```python
    sendSkillStr(ser, 'kjmp')
    ```

17. **Kick** (`kc`)

    ```python
    sendSkillStr(ser, 'kkc')
    ```

18. **Leap Over** (`lpov`)

    ```python
    sendSkillStr(ser, 'klpov')
    ```

19. **Moon Walk** (`mw`)

    ```python
    sendSkillStr(ser, 'kmw')
    ```

20. **Nod** (`nd`)

    ```python
    sendSkillStr(ser, 'knd')
    ```

21. **Play Dead** (`pd`)

    ```python
    sendSkillStr(ser, 'kpd')
    ```

22. **Pee** (`pee`)

    ```python
    sendSkillStr(ser, 'kpee')
    ```

23. **Push Ups** (`pu`)

    ```python
    sendSkillStr(ser, 'kpu')
    ```

24. **Push Ups with One Hand** (`pu1`)

    ```python
    sendSkillStr(ser, 'kpu1')
    ```

25. **Recover** (`rc`)

    ```python
    sendSkillStr(ser, 'krc')
    ```

26. **Roll** (`rl`)

    ```python
    sendSkillStr(ser, 'krl')
    ```

27. **Scratch** (`scrh`)

    ```python
    sendSkillStr(ser, 'kscrh')
    ```

28. **Sniff** (`snf`)

    ```python
    sendSkillStr(ser, 'ksnf')
    ```

29. **Be Table** (`tbl`)

    ```python
    sendSkillStr(ser, 'ktbl')
    ```

30. **Test** (`ts`)

    ```python
    sendSkillStr(ser, 'kts')
    ```

31. **Wave Head** (`wh`)

    ```python
    sendSkillStr(ser, 'kwh')
    ```

32. **All Joints at 0 Degrees** (`zz`)

    ```python
    sendSkillStr(ser, 'kzz')
    ```

## Additional Resources

For more information on using the Petoi Bittle Robot Dog and detailed documentation on the serial protocols, please refer to the [Petoi documentation](https://docs.petoi.com/).

