# v42-notify CSS edit for Survival Theme [QB/ESX]

Changed to allow backgrounds, sizing and sound effect to fit Zombie Survival theme

Showcase Medal: https://medal.tv/games/screen-capture/clips/1GT8aKNxfId_jx/d1337n8G4HoK?invite=cr-MSxPVG0sNDY1NTI5Mjgs

![notify-thumb](https://cdn.discordapp.com/attachments/1022431283487449099/1180303669581840414/image.png?ex=657cee73&is=656a7973&hm=5b0c28691701edc00314f6517ec9de3ac5258bab3c38343f406c3c3375f31283&)


### QBCore Manual

- Change the following line in qb-core/client/functions.lua default line 88: 

Replace this functions:
```
function QBCore.Functions.Notify(text, texttype, length)
    if type(text) == "table" then
        local ttext = text.text or 'Placeholder'
        local caption = text.caption or 'Placeholder'
        texttype = texttype or 'primary'
        length = length or 5000
        SendNUIMessage({
            action = 'notify',
            type = texttype,
            length = length,
            text = ttext,
            caption = caption
        })
    else
        texttype = texttype or 'primary'
        length = length or 5000
        SendNUIMessage({
            action = 'notify',
            type = texttype,
            length = length,
            text = text
        })
    end
end
```

Replace the above code with the following:

```
function QBCore.Functions.Notify(text, texttype, length)
    exports['v42-notify']:notify(text, texttype, length);
end
```

**Press F8 and type the following:**
```
ensure v42-notify
```

QBCore usage:
QBCore.Functions.Notify("messagge here", 'success', 5000)

### ESX Manual

- Change the following line in es_extended/client/functions.lua default line 73: 

Replace these function:
```
function ESX.ShowNotification(message, notifyType, length)
    if GetResourceState("esx_notify") ~= "missing" then
        return exports['esx-notify']:Notify(message, notifyType, length);
    end

    print("[^1ERROR^7] ^5ESX Notify^7 is Missing!")
end
```

Replace the above code with the following:

```
function ESX.ShowNotification(message, notifyType, length)
    if GetResourceState("v42-notify") ~= "missing" then
        return exports['v42-notify']:notify(message, notifyType, length);
    end

    print("[^1ERROR^7] ^5v42-notify^7 is Missing!")
end
```

**Enable EsxNotifcation option in the config.lua**

**Press F8 and type the following:**
```
ensure v42-notify
```

ESX Usage:
ESX.ShowNotification("message here", "success", 5000);

Create custom Notifications in the config.lua
```
['error'] = {
    icon = 'fas fa-exclamation-triangle', -Custom icon (fontawesome)
    sound = "sound.mp3", - Custom .mp3 sound
    color = '#FF0045', - Custom notify color
    volume = "0.3", - Sound volume
    mute = false, - Sound muted set to true
},
```
**ALL CREDITS TO ORIGINAL V42-Josh**
