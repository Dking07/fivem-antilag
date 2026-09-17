# ANTILAG AND 2STEP [STANDALONE]

<div align="center">
<img src="https://github.com/user-attachments/assets/441cc802-c8b2-41f2-9796-90a2d68abaef" alt="Thumbnail" width="700px" />
</div>

## DESCRIPTION

Bring realistic exhaust visual and sound effects to your FiveM server with this **Anti-Lag & 2-Step System**. Engineered for both standalone servers and economic roleplay environments, this script adds high-immersion exhaust backfires, flame bursts, and custom detonations.

> **NOTE:** All systems (Anti-Lag, 2-Step, and Flat-Shift) are **strictly visual and sound effects (PTFX & Audio)**. They do not alter vehicle handling, speed, acceleration, or physics in any way.

Featuring 12 custom addon `.awc` audio soundsets attached directly to vehicle entities (with full support to add more), 6 custom flame effects including pre-defined, RGB-compatible, and rainbow cycle modes (also expandable), and an integrated 3D orbital Position Editor (`/antilagpos`), this script gives you complete control over exhaust effects.

## KEY FEATURES

### **Audiovisual Exhaust Systems**
- **Anti-Lag**: Visual backfire flames and detonations triggered during high-RPM deceleration and off-throttle moments.
- **2-Step**: Stationary RPM limit effects producing synchronized flame bursts and rapid exhaust pops.
- **Flat-Shift**: Exhaust backfires and pops during gear shifts without lifting off the throttle, with duration dynamically matched to vehicle shift timing.

### **Dual Operating Architecture**
- **Standalone Mode (`'ALONE'`)**: Plug-and-play operation with KVP persistence, ox_lib input dialogs, and zero database requirements.
- **Roleplay Mode (`'RP'`)**: Physical item installation by mechanics, OneSync StateBag synchronization, and vehicle plate persistence via `oxmysql`.

### **Custom Flame Effects & RGB System**
- **6 Custom Flame Effects**:
  - **3 Pre-defined Styles**: Unique custom exhaust flames (`custom1`, `custom2`, `custom3`).
  - **3 RGB-Compatible Styles**: Full custom color picker support (`rgb1`, `rgb2`, `rgb3`).
  - **3 Rainbow Modes**: Dynamic spectrum color cycling with adjustable speed (`rainbow1`, `rainbow2`, `rainbow3`).
- **Expandable**: Easily add more particle dictionaries and flame styles in `config/flames.lua`.

### **High-Fidelity 3D Positional Audio**
- **12 Custom Sound Effects**: Packed with 12 distinct high-quality sound styles loaded via `audiodirectory/dking01antilag`.
- **Entity Attachment**: Real-time 3D audio originating directly from the vehicle entity exhausts.
- **Expandable**: Fully modular configuration allowing you to add more sound sets in `config/sounds.lua`.

### **3D Position Editor Tool**
- **Orbital Camera**: Full 3D camera navigation around the vehicle for exhaust particle offset calibration.
- **Visual Markers**: Interactive bounding spheres and live adjustment steps with automatic `effectPosition.json` export.

## GET NOW

* [DOWNLOAD](https://dking.tebex.io/package/7680077)

## HOW TO INSTALL

1. [Download](https://portal.cfx.re/assets/granted-assets) the script;
2. Place the `dking_antilag` folder in your server's `resources` directory;
3. Ensure you have `ox_lib` installed and started;
4. Add `ensure dking_antilag` to your `server.cfg`.

> **Note for RP Mode**: If running `Config.Mode = 'RP'`, ensure `oxmysql` are started before `dking_antilag`.

## HOW TO USE

### Standalone Mode (`Config.Mode = 'ALONE'`)
- `/antilag` - Open the Anti-Lag configuration dialog (toggle system, flat-shift, flame size, explosion speed, RPM threshold, sound style, RGB/Rainbow).
- `/2step` - Open the 2-Step dialog.
- `/antilagpreview [1 = Antilag, 2 = 2-Step]` - Active/Deactive a live visual and sound preview of current settings.
- `/antilagpos` - Open the developer 3D Position Editor to align exhaust flame coordinates (restricted by ACE `antilagPos`).

### Roleplay Mode (`Config.Mode = 'RP'`)
1. Mechanics approach the front of a vehicle with an open hood;
2. Use the inventory item (`antilag_module`, `twostep_module`, or `flatshift_chip`) to install the hardware;
3. Tuners use the `ecu_programmer` item inside the vehicle to adjust parameters;
4. Settings and module states automatically save to the database by vehicle plate.

## EXPORTS

<details>
  <summary><h2 style="display: inline;">Expand Exports API</h2></summary>

### Client Exports

| Export | Description | Return |
|---|---|---|
| `exports['dking_antilag']:SetAntilagState(state)` | Enables or disables antilag on current vehicle | `boolean` |
| `exports['dking_antilag']:GetAntilagState()` | Gets current antilag state | `boolean` |
| `exports['dking_antilag']:SetFlatShiftState(state)` | Enables or disables flat-shift on current vehicle | `boolean` |
| `exports['dking_antilag']:GetFlatShiftState()` | Gets current flat-shift state | `boolean` |
| `exports['dking_antilag']:SetTwoStepState(state)` | Enables or disables 2-step on current vehicle | `boolean` |
| `exports['dking_antilag']:GetTwoStepState()` | Gets current 2-step state | `boolean` |
| `exports['dking_antilag']:GetAntilagFullState()` | Returns complete runtime state snapshot | `table` |
| `exports['dking_antilag']:OpenAntilagMenu()` | Opens the Anti-Lag configuration menu | `void` |
| `exports['dking_antilag']:OpenTwoStepMenu()` | Opens the 2-Step configuration menu | `void` |
| `exports['dking_antilag']:UseInstallItem(item)` | Usable item handler for ox_inventory | `void` |

### Server Exports

| Export | Description | Return |
|---|---|---|
| `exports['dking_antilag']:SetPlayerAntilagState(playerId, state)` | Sets antilag state for specific player | `boolean` |
| `exports['dking_antilag']:SetPlayerFlatShiftState(playerId, state)` | Sets flat-shift state for specific player | `boolean` |
| `exports['dking_antilag']:SetPlayerTwoStepState(playerId, state)` | Sets 2-step state for specific player | `boolean` |
| `exports['dking_antilag']:InstallVehicleModule(vehicleNetId, moduleType)` | Installs module (`antilag`, `twoStep`, `flatShift`) | `boolean, string` |
| `exports['dking_antilag']:RemoveVehicleModule(vehicleNetId, moduleType)` | Uninstalls module from vehicle | `boolean, string` |
| `exports['dking_antilag']:HasVehicleModule(vehicleNetId, moduleType)` | Checks if vehicle has module installed | `boolean` |
| `exports['dking_antilag']:LoadVehicleData(vehicleNetId, plate)` | Loads vehicle tuning from database | `void` |

</details>

## CONFIGURATION

The resource provides granular modular configuration split across `config/`:
- `config/config.lua`: Master settings (`Config.Mode`, debug flags, KVP save mode, UI themes).
- `config/antilag.lua`: Default RPM threshold, explosion intervals, flame size, and rainbow cycle speeds.
- `config/2step.lua`: Cut RPM, flame sizing, and timing settings.
- `config/roleplay.lua`: Database table name, inventory item IDs, mechanic animation timings, and default ECU configurations.
- `config/flames.lua`: Particle dictionary mappings, RGB presets, rainbow cycle styles, and custom effect additions.
- `config/sounds.lua`: 12 sound sets mapped to `dking01antilag` audio bank, with support for adding new sound sets.
- `config/commands.lua`: Command names, descriptions, ACE permissions, and keybind definitions.

## PREVIEW

* [YouTube](https://youtu.be/Jsi1vPkXicE)

## DEPENDENCIES

* [ox_lib](https://github.com/overextended/ox_lib) (Required in both `ALONE` and `RP` modes for menus, dialogs, and notifications)
* [oxmysql](https://github.com/overextended/oxmysql) (Required only when running in Roleplay Mode: `Config.Mode = 'RP'`)

## SUPPORT

### [Discord](https://discord.gg/Rw6vjcXspG)

## CHANGELOGS

<details>
  <summary><h2 style="display: inline;">Expand Changelogs</h2></summary>

  <details>
    <summary style="margin-left: 20px;"><h3 style="display: inline;">1.0.0</h3></summary>
    <ul style="margin-left: 20px;">
      <li>Initial release;</li>
      <li>Individual client activation and KVP persistence;</li>
      <li>Audiovisual anti-lag, 2-step, and flat-shift effects (pure cosmetic, no physics alteration);</li>
      <li>Custom flame size, explosion speed, RPM threshold, and sound selection;</li>
      <li>12 entity-attached 3D sound sets from custom AWC wavepack (extensible);</li>
      <li>6 custom flame effects: 3 pre-defined, 3 RGB-compatible, 3 rainbow modes (extensible);</li>
      <li>Integrated 3D orbital exhaust Position Editor (<code>/antilagpos</code>);</li>
      <li>Dual-mode architecture (<code>'ALONE'</code> Standalone vs <code>'RP'</code> Roleplay);</li>
      <li>Mechanic physical installation system and StateBag synchronization;</li>
      <li>Complete Client and Server integration exports API.</li>
    </ul>
  </details>
</details>

# COPYRIGHT

## BY [DKING](https://github.com/Dking07) 2026 ©