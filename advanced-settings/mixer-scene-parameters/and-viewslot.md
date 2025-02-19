---
description: >-
  Enables viewing a specific slot from a scene link when the director is using
  &slotmode
---

# \&viewslot

The `&viewslot` parameter enables viewing a specific slot from a scene link when the director is using `&slotmode`. This creates a single-video view of whatever is assigned to that slot number.

## Usage

Basic syntax for viewing a specific slot:\
\
`/?scene&viewslot=1&room=ROOMNAME`

## Key Features

The `&viewslot` parameter provides single-video viewing of slot assignments with these characteristics:

* Only shows content from the specified slot number
* Dynamically updates when directors change slot assignments
* Optimizes performance by only loading the visible video stream
* Disables layouts and auto-mixing functionality
* Requires director to be using `&slotmode`

## Performance Optimization

By default, only the visible video stream is connected to reduce CPU and network load. Two parameters control this behavior:

```
&nohiddensceneoptimization    # Prevents optimization of hidden elements
&hiddenscenebitrate=VALUE     # Sets custom bitrate for hidden videos (default: 0)
```

## Related Parameters

#### Slot Assignment (`&slot`)

Guests can specify their preferred slot assignment:

```
&slot=N    # N is the desired slot number
```

)![Image](https://media.discordapp.net/attachments/701232125831151697/1223142944123654144/image.png?ex=67b6bea2\&is=67b56d22\&hm=2f2e9443ff8abdf9fd04d6823c71300e91499b0f764274fc8dec9eaa6bdebd4a&=\&format=webp\&quality=lossless\&width=486\&height=257)

### Fixed Slot Count (`&slots`)

Forces a specific number of slots in the auto-mixer:

```
&slots=N    # N is the desired number of slots
```

### Slot Mode (`&slotmode`)

Director parameter enabling slot assignment functionality:

```
&slotmode    # Enables slot management for directors
```
