# RiShade

Runs ReShade directly inside Voidstrap's compositor without injecting into Roblox. Based on [Unishade](https://github.com/OMouta/Unishade) by OMouta (huge credit to him for his original work in C++).

## How it works

Voidstrap captures the Roblox window with Windows Graphics Capture (WGC) and runs ReShade 6.8 effects directly on D3D11 swapchain frames in the compositor before Anti-Aliasing, motion blur, and Frame Gen. No hooks or DLL injection into Roblox.

On first enable, Voidstrap grabs ReShade 6.8 and official shader packs into `Extensions/RiShade`, keeping your existing presets and configs safe.

## Remote desktops

The RiShade menu stays visible to recording and remote desktop software, including Shadow. When Windows Graphics Capture is unavailable, opening the menu pauses monitor capture and displays the last captured game frame behind the menu. Closing the menu resumes capture. This prevents the compositor from capturing itself while the menu is visible. The fallback game output remains excluded from capture when the menu is closed.

The menu also redraws when window capture has no new frames, such as when Roblox is idle or loses focus. Until frames resume, the menu uses the last captured game frame as its background.

## Building

```sh
cargo build --release --manifest-path native/rishade/Cargo.toml
```

## Credits

- [Unishade](https://github.com/OMouta/Unishade) by OMouta
- [ReShade](https://reshade.me) by crosire
