---
Description: Specifies which audio devices the Voice Capture DSP uses for capturing and rendering audio.
ms.assetid: 42b6b82b-ac64-4a07-956c-473dd57a128d
title: MFPKEY\_WMAAECMA\_DEVICE\_INDEXES Property
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# MFPKEY\_WMAAECMA\_DEVICE\_INDEXES Property

Specifies which audio devices the Voice Capture DSP uses for capturing and rendering audio.

## Constant for IPropertyBag

Available only by using [**IPropertyStore**](https://msdn.microsoft.com/e995aaa1-d4c9-475f-b1fa-b9123cd5b653).

## Data Type

VT\_I4

## Default Value

(-1, -1).

## Applies To

-   [Voice Capture DSP](voicecapturedmo.md)

## Remarks

Set this property if you are using the DSP in source mode. The DSP ignores this property in filter mode.

The value of the property is two 16-bit **WORD**s packed into a **DWORD**. The upper 16 bits specify the audio rendering device (typically a speaker), and the lower 16 bits specify the capture device (typically a microphone). Each device is specified as an index into the audio device collection. If the index is -1, the default device is used.

The device index corresponds to the collection index used in the [**IMMDeviceCollection**](https://msdn.microsoft.com/4769b0a6-a319-4605-8742-5e7c285679cf) interface. The application must play the far-end voice through the selected rendering device. (The far-end voice is the voice of the person on the other end of the telephone line, which is played through the speaker on the user's computer.) If the selected rendering device does not have an active stream, the DSP cannot process any output.

The default value of this property is (-1, -1).

The following example shows how to initialize the **PROPVARIANT** for this property.


```
int iSpeakerIndex = -1;
int iMicrophoneIndex = -1;

// Find the device indexes to initialize iSpeakerIndex and 
// iMicrophone index (not shown).

PROPVARIANT varDeviceIndexes;
PropVariantInit(&amp;varDeviceIndexes);
varDeviceIndexes.vt = VT_I4;
varDeviceIndexes.lVal = (unsigned long)(iSpeakerIndex << 16) + 
    (unsigned long)(0x0000ffff & iMicrophoneIndex);
```



## Requirements



|                                     |                                                                                         |
|-------------------------------------|-----------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows Vista \[desktop apps only\]<br/>                                          |
| Minimum supported server<br/> | Windows Server 2008 \[desktop apps only\]<br/>                                    |
| Header<br/>                   | <dl> <dt>Wmcodecdsp.h</dt> </dl> |



## See also

<dl> <dt>

[Media Foundation Properties](media-foundation-properties.md)
</dt> <dt>

[Voice Capture DSP](voicecapturedmo.md)
</dt> </dl>

 

 



