#Requires AutoHotkey v2.0
InstallKeybdHook() ; Klavyeyi daha hassas dinlemesini sağlar

; Caps Lock ışığını ve fonksiyonunu tamamen kapat
SetCapsLockState "AlwaysOff"

*CapsLock::
{
    ; Caps'e basıldığında Control'ü basılı tut
    Send "{LControl Down}"
    
    ; Caps'in bırakılmasını bekle
    KeyWait "CapsLock"
    
    ; Bırakıldığında Control'ü de bırak
    Send "{LControl Up}"

    ; Eğer basılıyken başka hiçbir tuşa basılmadıysa (Tap durumu)
    if (A_PriorKey = "CapsLock")
    {
        Send "{Esc}"
    }
}
