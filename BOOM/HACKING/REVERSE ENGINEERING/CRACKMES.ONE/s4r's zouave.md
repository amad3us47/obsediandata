

push    43h ; 'C'       ; cchMax
push    offset byte_4020A4 ; lpString
push    3F6h            ; nIDDlgItem
push    [ebp+hWnd]      ; hDlg
call    ds:GetDlgItemTextA
call    sub_4018F7
cmp     eax, 1
<span style="color:rgb(0, 176, 80)">jnz  </span>   short loc_401857



TO 


push    43h ; 'C'       ; cchMax
push    offset byte_4020A4 ; lpString
push    3F6h            ; nIDDlgItem
push    [ebp+hWnd]      ; hDlg
call    ds:GetDlgItemTextA
call    sub_4018F7
cmp     eax, 1
<span style="color:rgb(0, 176, 80)">jz </span>     short loc_401857