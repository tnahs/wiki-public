# Apple Symbolic Hotkeys

The default macOS hotkeys found in `System Preferences` > `Keyboard` are located in the `com.apple.symbolichotkeys.plist` inside `~/Library/Preferences`.

## Structure

```plaintext
{
    AppleSymbolicHotKeys = {

        <action:int> = Dict {
            enabled = <enabled:bool>
            value = Dict {
                type = <type:string>
                parameters = Array {
                    <0:int>
                    <1:int>
                    <2:int>
                }
            }
        },

        ...

    }
}
```

## Definition

```plaintext
action: The ID of action the hotkey will take.
    enabled: Toggle enabled/disabled.
    value:
        type: Always seems to be 'standard'...
        parameters:
            0: ASCII code of the character or '65535' for non-ASCII characters.
            1: AppleScript key code for the character.
            2: Summed value of the modifier keys.*
```

\* See [Modifiers](#modifiers).

## Key Codes

### Characters

Use an application like [KeyCodes](https://manytricks.com/keycodes/) to retrieve character key codes for `action:value:parameters:0` and `action:value:parameters:1`.

### Modifiers

Modifier key codes for `action:value:parameters:2`:

| Key     | Code    |
| ------- | ------- |
| Control | 26214   |
| Option  | 524288  |
| Shift   | 131072  |
| Command | 1048576 |
| None    | 0       |

With key combinations being the sum of their respective codes. For example:

    Command + Shift -> 1048576 + 131072 -> 1179648

## Edit Using PlistBuddy

```shell
HOTKEYS_PLIST=$HOME/Library/Preferences/com.apple.symbolichotkeys.plist

# Move right a space - Command+Shift+D
/usr/libexec/PlistBuddy -c "Set :AppleSymbolicHotKeys:79:enabled true" $HOTKEYS_PLIST
/usr/libexec/PlistBuddy -c "Set :AppleSymbolicHotKeys:79:value:parameters:0 97" $HOTKEYS_PLIST
/usr/libexec/PlistBuddy -c "Set :AppleSymbolicHotKeys:79:value:parameters:1 0" $HOTKEYS_PLIST
/usr/libexec/PlistBuddy -c "Set :AppleSymbolicHotKeys:79:value:parameters:2 1179648" $HOTKEYS_PLIST
```

## Keys Reference

Taken from [Documenting com.apple.symbolichotkeys.plist](https://web.archive.org/web/20141112224103/http://hintsforums.macworld.com/showthread.php?t=114785) dated 11-09-2010.

```swift
{
    AppleSymbolicHotKeys = {

        // Move focus to the menu bar - Control, F2
        7 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    120,
                    262144
                );
                type = standard;
            };
        };

        // Move focus to the Dock - Control, F3
        8 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    99,
                    262144
                );
                type = standard;
            };
        };

        // Move focus to active or next window - Control, F4
        9 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    118,
                    262144
                );
                type = standard;
            };
        };

        // Move focus to window toolbar - Control, F5
        10 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    96,
                    262144
                );
                type = standard;
            };
        };

        // Move focus to floating window - Control, F6
        11 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    97,
                    262144
                );
                type = standard;
            };
        };

        // ??? - Control, F1
        12 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    122,
                    262144
                );
                type = standard;
            };
        };

        // Change the way Tab moves focus - Control, F7
        13 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    98,
                    262144
                );
                type = standard;
            };
        };

        // Turn zoom on or off - Command, Option, 8
        15 = {
            enabled = 1;
            value = {
                parameters = (
                    56,
                    28,
                    1572864
                );
                type = standard;
            };
        };

        // Zoom in - Command, Option, =
        17 = {
            enabled = 0;
            value = {
                parameters = (
                    61,
                    24,
                    1572864
                );
                type = standard;
            };
        };

        // Zoom out - Command, Option, -
        19 = {
            enabled = 0;
            value = {
                parameters = (
                    45,
                    27,
                    1572864
                );
                type = standard;
            };
        };

        // Reverse Black and White - Command, Control, Option, 8
        21 = {
            enabled = 1;
            value = {
                parameters = (
                    56,
                    28,
                    1835008
                );
                type = standard;
            };
        };

        // Turn image smoothing on or off - Command, Option, \
        23 = {
            enabled = 0;
            value = {
                parameters = (
                    92,
                    42,
                    1572864
                );
                type = standard;
            };
        };

        // Increase Contrast - Command, Control, Option, .
        25 = {
            enabled = 1;
            value = {
                parameters = (
                    46,
                    47,
                    1835008
                );
                type = standard;
            };
        };

        // Decrease Contrast - Command, Control, Option, ','
        26 = {
            enabled = 1;
            value = {
                parameters = (
                    44,
                    43,
                    1835008
                );
                type = standard;
            };
        };

        // Move focus to the next window in application - Command, backtic
        27 = {
            enabled = 1;
            value = {
                parameters = (
                    96,
                    50,
                    1048576
                );
                type = standard;
            };
        };

        // Save picture of screen as file - Command, Shift, 3
        28 = {
            enabled = 1;
            value = {
                parameters = (
                    51,
                    20,
                    1179648
                );
                type = standard;
            };
        };

        // Copy picture of screen to clipboard - Command, Control, Shift, 3
        29 = {
            enabled = 1;
            value = {
                parameters = (
                    51,
                    20,
                    1441792
                );
                type = standard;
            };
        };

        // Save picture of selected area as file - Command, Shift, 4
        30 = {
            enabled = 1;
            value = {
                parameters = (
                    52,
                    21,
                    1179648
                );
                type = standard;
            };
        };

        // Copy picture of selected area to clipboard - Command, Control, Shift, 4
        31 = {
            enabled = 1;
            value = {
                parameters = (
                    52,
                    21,
                    1441792
                );
                type = standard;
            };
        };

        // All Windows - F9
        32 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    101,
                    0
                );
                type = standard;
            };
        };

        // Application Windows - F10
        33 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    109,
                    0
                );
                type = standard;
            };
        };

        // All Windows (Slow) - F9
        34 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    101,
                    131072
                );
                type = standard;
            };
        };

        // Application Windows (Slow) - F10
        35 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    109,
                    131072
                );
                type = standard;
            };
        };

        // Desktop - F11
        36 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    103,
                    0
                );
                type = standard;
            };
        };

        // Desktop (Slow) - F11
        37 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    103,
                    131072
                );
                type = standard;
            };
        };

        // ??? - Command, Option, T
        50 = {
            enabled = 1;
            value = {
                parameters = (
                    116,
                    17,
                    1572864
                );
                type = standard;
            };
        };

        // Move focus to the window drawer - Command, Option, quote
        51 = {
            enabled = 1;
            value = {
                parameters = (
                    39,
                    50,
                    1572864
                );
                type = standard;
            };
        };

        // Turn Dock Hiding On/Off - Command, Option, D
        52 = {
            enabled = 1;
            value = {
                parameters = (
                    100,
                    2,
                    1572864
                );
                type = standard;
            };
        };

        // ??? - F14
        53 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    107,
                    0
                );
                type = standard;
            };
        };

        // ??? - F15
        54 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    113,
                    0
                );
                type = standard;
            };
        };

        // ??? - Option, F14
        55 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    107,
                    524288
                );
                type = standard;
            };
        };

        // ??? - Option, F15
        56 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    113,
                    524288
                );
                type = standard;
            };
        };

        // Move focus to the status menus - Control, F8
        57 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    100,
                    262144
                );
                type = standard;
            };
        };

        // Turn VoiceOver on / off - Command, F5
        59 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    96,
                    1048576
                );
                type = standard;
            };
        };

        // Select the previous input source - Command, Option, Space
        60 = {
            enabled = 1;
            value = {
                parameters = (
                    32,
                    49,
                    1572864
                );
                type = standard;
            };
        };

        // Select the next source in the Input Menu - Command, Option, Shift, Space
        61 = {
            enabled = 1;
            value = {
                parameters = (
                    32,
                    49,
                    1703936
                );
                type = standard;
            };
        };

        // Dashboard - F12
        62 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    111,
                    0
                );
                type = standard;
            };
        };

        // Dashboard (Slow) - F12
        63 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    111,
                    131072
                );
                type = standard;
            };
        };

        // Show Spotlight search field - Command, Shift, Space
        64 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    49,
                    1179648
                );
                type = standard;
            };
        };

        // Show Spotlight window - Control, Shift, Space
        65 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    49,
                    393216
                );
                type = standard;
            };
        };

        // Dictionary MouseOver - Command, Shift, E
        70 = {
            enabled = 1;
            value = {
                parameters = (
                    101,
                    2,
                    1179648
                );
                type = standard;
            };
        };

        // Hide and show Front Row - Command, Esc
        73 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    53,
                    1048576
                );
                type = standard;
            };
        };

        // Activate Spaces - F8
        75 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    100,
                    0
                );
                type = standard;
            };
        };

        // Activate Spaces (Slow) - Shift, F8
        76 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    100,
                    131072
                );
                type = standard;
            };
        };

        // Spaces Left - Control, Left
        79 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    123,
                    262144
                );
                type = standard;
            };
        };

        // Spaces Right - Control, Right
        81 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    124,
                    262144
                );
                type = standard;
            };
        };

        // Spaces Down - Control, Down
        83 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    125,
                    262144
                );
                type = standard;
            };
        };

        // Spaces Up - Control, Up
        85 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    126,
                    262144
                );
                type = standard;
            };
        };

        // Show Help Menu - Command, Shift, /
        91 = { enabled = 0; };
        92 = { enabled = 0; };
        98 = {
            enabled = 0;
            value = {
                parameters = (
                    47,
                    44,
                    1179648
                );
                type = standard;
            };
        };

        // Switch to Space 1 - Control, 1
        118 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    18,
                    262144
                );
                type = standard;
            };
        };

        // Switch to Space 2 - Control, 2
        119 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    19,
                    262144
                );
                type = standard;
            };
        };

        // Switch to Space 3 - Control, 3
        120 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    20,
                    262144
                );
                type = standard;
            };
        };

        // Switch to Space 4 - Control, 4
        121 = {
            enabled = 1;
            value = {
                parameters = (
                    65535,
                    21,
                    262144
                );
                type = standard;
            };
        };

        122 = { enabled = 0; };
        123 = { enabled = 0; };
        124 = { enabled = 0; };
        125 = { enabled = 0; };
        126 = { enabled = 0; };
        127 = { enabled = 0; };
        128 = { enabled = 0; };
        129 = { enabled = 0; };
        130 = { enabled = 0; };
        131 = { enabled = 0; };
        132 = { enabled = 0; };
        133 = { enabled = 0; };
        134 = { enabled = 0; };
        135 = { enabled = 0; };
        136 = { enabled = 0; };
        137 = { enabled = 0; };
        138 = { enabled = 0; };
        139 = { enabled = 0; };
        140 = { enabled = 0; };
        141 = { enabled = 0; };
        142 = { enabled = 0; };
        143 = { enabled = 0; };
        144 = { enabled = 0; };
        145 = { enabled = 0; };
        146 = { enabled = 0; };
        147 = { enabled = 0; };
        148 = { enabled = 0; };
        149 = { enabled = 0; };
    };
}
```

<!--
# 71 Cycle through active applications - middle mouse button
defaults write com.apple.symbolichotkeys AppleSymbolicHotKeys -dict-add 71 '{ enabled = 0; value = { parameters = (
    4,
    4,
    0
); type = button; }; }'

As you see, 'type' is not always 'standard'.
-->

## References

- [What do the parameter values in AppleSymbolicHotKeys plist dict represent?](https://stackoverflow.com/q/21878482)
- [Defaults & symbolichotkeys in Mac OS X](https://krypted.com/mac-os-x/defaults-symbolichotkeys/)
