# 2026 KitBot Code

WPILib robot code for the 2026 FRC KitBot — differential drive with a fuel intake and launcher.

## Setup

- Install [WPILib 2026](https://docs.wpilib.org/)
- Open this folder in VS Code with the WPILib extension
- Set your team number in `.wpilib/wpilib_preferences.json` (currently **21301**)
- Deploy with **WPILib: Deploy Robot Code** or `./gradlew deploy`

## Controls

Xbox controller on USB port **0**.

| Input         | Action                    |
|---------------|---------------------------|
| Left stick    | Drive                     |
| Right stick   | Turn                      |
| Left bumper   | Intake                    |
| Right bumper  | Spin up, then launch      |
| A             | Eject                     |
| B             | Launch (alternate speed)  |

## Operating the Robot

Edit this section for your team's workflow.

### Before the match

1. Power on the robot and confirm the roboRIO connects in Driver Station
2. Check battery voltage — TODO: add your minimum voltage
3. Confirm fuel is loaded — TODO: describe how much / where
4. Select autonomous mode on the SmartDashboard — TODO: add routine names
5. Place the robot on the field — TODO: add starting position

### Autonomous

1. Enable autonomous when the match starts
2. TODO: describe what the robot should do (e.g. drive back, shoot fuel)
3. TODO: add any notes for drivers (stay clear, watch for X, etc.)

### Teleop

1. Take over when teleop begins
2. Drive to pick up fuel — TODO: add your preferred approach
3. Hold **left bumper** to intake
4. Hold **right bumper** to spin up and launch
5. Use **A** to eject if fuel gets stuck
6. TODO: add scoring / defense / endgame steps

### After the match

1. Disable the robot in Driver Station
2. Power off or switch to disabled — TODO: add your pit procedure
3. Check for loose wiring or jammed fuel — TODO: add inspection checklist

## Tuning

Fuel roller voltages can be adjusted on the SmartDashboard during practice. Copy good values into `Constants.java` when done.

## License

WPILib is BSD 3-Clause. See [WPILib-License.md](WPILib-License.md).
