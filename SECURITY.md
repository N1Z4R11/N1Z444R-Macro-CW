# Security and API usage

This document explains the Windows APIs visible in static analysis of the official N1Z444R Macro CW build.

## `GetAsyncKeyState`

Used only with the virtual-key values for the left, right, or middle **mouse buttons** to confirm that a macro-generated hold was accepted and later released. The application does not poll alphanumeric keys, build keystroke logs, or transmit keyboard input.

## `CopyFromScreen`

Used to capture the pixels inside the Roblox client rectangle into an in-memory bitmap. The bitmap is analyzed locally for the pause menu, Friends Online, Daily Spins, Round Ended, and CLOSE controls, then disposed. These captures are not uploaded or transmitted.

## `WebClient` / `DownloadStringTaskAsync`

Used for an HTTPS GET request to the hard-coded Roblox public-server endpoint:

`https://games.roblox.com/v1/games/{placeId}/servers/Public`

The JSON response is used only to select an eligible public server. The application does not download or execute programs.

## Process launching

Used to open Roblox join links and the local text log. It is not used to install services, create startup persistence, or execute downloaded payloads.

## Network behavior

The application contains no upload endpoint, remote shell, command-and-control client, email sender, socket listener, or remote-access feature. The official build string does not contain a standalone `RAT` marker.

## Build policy

The v1.0.0 clean baseline avoids aggressive anti-tamper and maximum-obfuscation presets because they caused antivirus heuristic detections. Authenticity is provided through the permanent N1Z444R watermark, assembly metadata, build ID, official release page, and published SHA-256 hashes.
