---
title: CBN\_DBLCLK notification code
description: Sent when the user double-clicks a string in the list box of a combo box. The parent window of the combo box receives this notification code through the WM\_COMMAND message.
ms.assetid: '79ca3fd3-4a71-4bd5-be68-efc867a4ad22'
keywords: ["CBN_DBLCLK notification code Windows Controls"]
topic_type:
- apiref
api_name:
- CBN_DBLCLK
api_location:
- Winuser.h
api_type:
- HeaderDef
---

# CBN\_DBLCLK notification code

Sent when the user double-clicks a string in the list box of a combo box. The parent window of the combo box receives this notification code through the [**WM\_COMMAND**](https://msdn.microsoft.com/library/windows/desktop/ms647591) message.


```C++
CBN_DBLCLK

    WPARAM wParam;
    LPARAM lParam; 
```



## Parameters

<dl> <dt>

*wParam* 
</dt> <dd>

The [**LOWORD**](https://msdn.microsoft.com/library/windows/desktop/ms632659) contains the control identifier of the combo box. The [**HIWORD**](https://msdn.microsoft.com/library/windows/desktop/ms632657) specifies the notification code.

</dd> <dt>

*lParam* 
</dt> <dd>

Handle to the combo box.

</dd> </dl>

## Remarks

This notification code occurs only for a combo box with the [**CBS\_SIMPLE**](combo-box-styles.md#cbs-simple) style. In a combo box with the [**CBS\_DROPDOWN**](combo-box-styles.md#cbs-dropdown) or [**CBS\_DROPDOWNLIST**](combo-box-styles.md#cbs-dropdownlist) style, a double-click cannot occur because a single click closes the list box.

## Requirements



|                                     |                                                                                                          |
|-------------------------------------|----------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows�Vista \[desktop apps only\]<br/>                                                           |
| Minimum supported server<br/> | Windows Server�2003 \[desktop apps only\]<br/>                                                     |
| Header<br/>                   | <dl> <dt>Winuser.h (include Windows.h)</dt> </dl> |



## See also

<dl> <dt>

**Reference**
</dt> <dt>

[CBN\_SELCHANGE](cbn-selchange.md)
</dt> <dt>

**Other Resources**
</dt> <dt>

[**HIWORD**](https://msdn.microsoft.com/library/windows/desktop/ms632657)
</dt> <dt>

[**LOWORD**](https://msdn.microsoft.com/library/windows/desktop/ms632659)
</dt> <dt>

[**WM\_COMMAND**](https://msdn.microsoft.com/library/windows/desktop/ms647591)
</dt> </dl>

�

�




