Separates a large class, or a set of related classes into two separate hierarchies so that they can be developed independently from each other.

## In Practice

### Bad Example

```cs
var lgRemote = new LGRemote();
lgRemote.TurnOn(); // Turning LG radio on
lgRemote.TurnOff(); // Turning LG radio off

var lgRadioAndTVLGRemote = new LGRadioAndTVLGRemote();
lgRadioAndTVLGRemote.ControlTV(); // Now controlling LG TV
lgRadioAndTVLGRemote.TurnOn(); // Turning LG device on
lgRadioAndTVLGRemote.VolumeUp(); // Turning LG device volume up
```

### Good Example

```cs
var lgRemoteControl = new RemoteControl(new LGRadio());
lgRemoteControl.TurnOn(); // Turning LG radio on
lgRemoteControl.TurnOff(); // Turning LG radio off

var advancedSonyControl = new AdvancedRemote(new SonyRadio());
advancedSonyControl.TurnOn(); // Turning Sony radio on
advancedSonyControl.TurnOff(); // Turning Sony radio off
```
