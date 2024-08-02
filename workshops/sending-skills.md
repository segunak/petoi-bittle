# Sending Skills

## The `sendSkillStr` Function

The `sendSkillStr` function is designed to send a specific skill command to the Petoi Robot, instructing it to perform a predefined action or movement. This function is part of the `PetoiRobot` module, which facilitates communication with the robot via serial commands.

## Parameters

- **skillStr** (str): This parameter is a string representing the skill command to be sent to the robot. Each skill corresponds to a specific action or movement that the robot can perform, such as sitting, standing, walking, or performing tricks like flips.
  
- **delayTime** (int): This parameter represents the delay time in milliseconds after the command is sent. The delay allows for proper execution timing of the skill, ensuring the robot has enough time to complete the action before receiving the next command.

## Usage Example

Here is an example of how to use the `sendSkillStr` function to make the robot sit:

```python
sendSkillStr("ksit", 1)
```

In this example:

- `"ksit"` is the skill command that instructs the robot to sit.
- `500` is the delay time in milliseconds, allowing the robot to execute the sit action for half a second before any other command is issued.

### Explanation of the Function

The `sendSkillStr` function sends a short skill string command to the robot via serial communication. This function uses the `send` function, which communicates with the robot's serial port, transmitting the skill command string and the specified delay time.

1. **Logging the Skill Command**: The function logs the skill command string (`skillStr`) for debugging purposes.

2. **Sending the Command**: The function calls the `send` function, passing the serial ports (`goodPorts`), the skill command string, and the delay time as a list.

3. **Delay Handling**: The delay time ensures that there is a proper interval between consecutive commands, allowing the robot to complete one action before starting another.

## Skills and Their Commands

Here is the list of all skills that can be sent using `sendSkillStr` and their corresponding commands. Each function is explained along with an example of its usage.

### Skills and Commands

1. **Sit**: `ksit`
   - **Description**: Makes the robot sit down.
   - **Example**: `sendSkillStr("ksit", 1)`

2. **Stand Up**: `kup`
   - **Description**: Makes the robot stand up.
   - **Example**: `sendSkillStr("kup", 1)`

3. **Bottom Up**: `kbuttUp`
   - **Description**: Raises the robot's bottom.
   - **Example**: `sendSkillStr("kbuttUp", 1)`

4. **Stretch**: `kstr`
   - **Description**: Stretches the robot.
   - **Example**: `sendSkillStr("kstr", 1)`

5. **Rest**: `krest`
   - **Description**: Puts the robot in a resting position.
   - **Example**: `sendSkillStr("krest", 1)`

6. **Zero**: `kzero`
   - **Description**: Resets the robot to its default position.
   - **Example**: `sendSkillStr("kzero", 1)`

7. **Boxing**: `kbx`
   - **Description**: Makes the robot perform boxing movements.
   - **Example**: `sendSkillStr("kbx", 1)`

8. **Cheer**: `kchr`
   - **Description**: Makes the robot cheer.
   - **Example**: `sendSkillStr("kchr", 1)`

9. **Check Around**: `kck`
   - **Description**: Makes the robot check its surroundings.
   - **Example**: `sendSkillStr("kck", 1)`

10. **Dig**: `kdg`
    - **Description**: Makes the robot dig.
    - **Example**: `sendSkillStr("kdg", 1)`

11. **Stand on Hands**: `khds`
    - **Description**: Makes the robot stand on its hands.
    - **Example**: `sendSkillStr("khds", 1)`

12. **Hug**: `khg`
    - **Description**: Makes the robot give a hug.
    - **Example**: `sendSkillStr("khg", 1)`

13. **Hi**: `khi`
    - **Description**: Makes the robot wave hello.
    - **Example**: `sendSkillStr("khi", 1)`

14. **Hands Up**: `khu`
    - **Description**: Makes the robot raise its hands.
    - **Example**: `sendSkillStr("khu", 1)`

15. **Jump**: `kjmp`
    - **Description**: Makes the robot jump.
    - **Example**: `sendSkillStr("kjmp", 1)`

16. **Kick**: `kkc`
    - **Description**: Makes the robot kick.
    - **Example**: `sendSkillStr("kkc", 1)`

17. **Nod**: `knd`
    - **Description**: Makes the robot nod.
    - **Example**: `sendSkillStr("knd", 1)`

18. **Play Dead**: `kpd`
    - **Description**: Makes the robot play dead.
    - **Example**: `sendSkillStr("kpd", 1)`

19. **Pee**: `kpee`
    - **Description**: Makes the robot simulate peeing.
    - **Example**: `sendSkillStr("kpee", 1)`

20. **Push Up**: `kpu`
    - **Description**: Makes the robot do push-ups.
    - **Example**: `sendSkillStr("kpu", 1)`

21. **Scratch**: `kscrh`
    - **Description**: Makes the robot scratch.
    - **Example**: `sendSkillStr("kscrh", 1)`

22. **Sniff**: `ksnf`
    - **Description**: Makes the robot sniff.
    - **Example**: `sendSkillStr("ksnf", 1)`

23. **Stepping**: `kvtF`
    - **Description**: Makes the robot perform a stepping movement.
    - **Example**: `sendSkillStr("kvtF", 1)`

24. **Crawl Forward**: `kcrF`
    - **Description**: Makes the robot crawl forward.
    - **Example**: `sendSkillStr("kcrF", 1)`

25. **Crawl Left**: `kcrL`
    - **Description**: Makes the robot crawl to the left.
    - **Example**: `sendSkillStr("kcrL", 1)`

26. **Crawl Right**: `kcrR`
    - **Description**: Makes the robot crawl to the right.
    - **Example**: `sendSkillStr("kcrR", 1)`

27. **Push Forward**: `kphF`
    - **Description**: Makes the robot push forward.
    - **Example**: `sendSkillStr("kphF", 1)`

28. **Push Left**: `kphL`
    - **Description**: Makes the robot push to the left.
    - **Example**: `sendSkillStr("kphL", 1)`

29. **Push Right**: `kphR`
    - **Description**: Makes the robot push to the right.
    - **Example**: `sendSkillStr("kphR", 1)`

30. **Walk Forward**: `kwkF`
    - **Description**: Makes the robot walk forward.
    - **Example**: `sendSkillStr("kwkF", 1)`

31. **Walk Left**: `kwkL`
    - **Description**: Makes the robot walk to the left.
    - **Example**: `sendSkillStr("kwkL", 1)`

32. **Walk Right**: `kwkR`
    - **Description**: Makes the robot walk to the right.
    - **Example**: `sendSkillStr("kwkR", 1)`

33. **Back**: `kbk`
    - **Description**: Makes the robot move backward.
    - **Example**: `sendSkillStr("kbk", 1)`

34. **Back Left**: `kbkL`
    - **Description**: Makes the robot move backward to the left.
    - **Example**: `sendSkillStr("kbkL", 1)`

35. **Back Right**: `kbkR`
    - **Description**: Makes the robot move backward to the right.
    - **Example**: `sendSkillStr("kbkR", 1)`

36. **Trot Forward**: `ktrF`
    - **Description**: Makes the robot trot forward.
    - **Example**: `sendSkillStr("ktrF", 1)`

37. **Trot Left**: `ktrL`
    - **Description**: Makes the robot trot to the left.
    - **Example**: `sendSkillStr("ktrL", 1)`

38. **Trot Right**: `ktrR`
    - **Description**: Makes the robot trot to the right.
    - **Example**: `sendSkillStr("ktrR", 1)`

39. **Back Flip**: `kbf`
    - **Description**: Makes the robot perform a backflip.
    - **Example**: `sendSkillStr("kbf", 1)`

40. **Front Flip**: `kff`
    - **Description**: Makes the robot perform a front flip.
    - **Example**: `sendSkillStr("kff", 1)`
