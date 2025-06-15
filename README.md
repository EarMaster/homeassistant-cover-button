# 🎮 One-Button Cover Control

A Home Assistant blueprint that allows you to control any cover, shade, blind, or garage door with a single button. Press once to open if closed, close if open or stop if currently moving.

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A//raw.githubusercontent.com/EarMaster/homeassistant-cover-button/main/button-cover.yaml)

## ✨ Features

- **Smart Logic**: Automatically determines the appropriate action based on current cover state
- **Universal Compatibility**: Works with most button devices and cover types
- **Flexible Button Support**: Compatible with any device that triggers an event (even if it's not technically a button)
- **Multiple Action Types**: Supports various actions (short press, long press, double press, etc.)
- **Entity/Device Actions**: Choose between device actions or entity service calls for maximum compatibility
- **Stop Function**: Automatically stops covers that are currently moving

## 🚀 Quick Start

### Installation

1. Click the "Add Blueprint to Home Assistant" button above, or
2. Manually add the blueprint:
   - Copy the contents of `button-cover.yaml`
   - Go to **Settings** → **Automations & Scenes** → **Blueprints**
   - Click **Import Blueprint** and paste the YAML content

### Configuration

1. Create a new automation using this blueprint
2. Select your button device
3. Choose the button action type (default: `remote_button_short_press`)
4. Select your cover entity
5. Optionally enable "Use Entity Actions" if device actions don't work

## 📋 Supported Devices

### Button Devices

- Any button/remote
- Single buttons, multi-button remotes
- Wall switches, handheld remotes, smart buttons

### Cover Types

- Window blinds and shades
- Curtains and drapes
- Awnings and outdoor covers
- Garage doors
- Any Home Assistant cover entity

## ⚙️ Configuration Options

| Parameter | Description | Default |
|-----------|-------------|---------|
| **Button Device** | The button or remote control device | Required |
| **Button Action** | The specific action to trigger (press, double-press, etc.) | `remote_button_short_press` |
| **Button Subtype** | Additional identifier if needed (button_1, button_2) | Empty |
| **Cover Entity** | The cover to control | Required |
| **Use Entity Actions** | Use service calls instead of device actions | `false` |

### Available Button Actions

- `remote_button_short_press`
- `remote_button_long_press`
- `remote_button_double_press`
- `key_press_1`, `key_press_2`, `key_press_3`, `key_press_4`
- `button_1`, `button_2`, `button_3`, `button_4`
- Custom values are also supported

## 🔧 How It Works

The blueprint uses intelligent logic to determine the appropriate action:

1. **If cover is moving** (opening/closing) → **Stop**
2. **If cover is open** → **Close**
3. **If cover is closed** → **Open**
4. **If cover is partially open** → **Toggle** (opens or closes based on device preference)

## 🛠️ Troubleshooting

### Cover Not Responding

- Try enabling "Use Entity Actions Instead of Device Actions"
- Verify your cover entity is working manually
- Check that your button device is properly paired

### Button Not Triggering

- Verify the button action type matches your device
- Check the device integration (ZHA/deCONZ/Zigbee2MQTT)
- Use Developer Tools → Events to monitor button presses

### Wrong Button on Multi-Button Remote

- Use the "Button Subtype" field to specify which button (e.g., "button_1")
- Check your device's available actions in Developer Tools

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

Made with ❤️ for the Home Assistant community
