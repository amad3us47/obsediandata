

loc_4014FD:
mov     eax, [ebp+var_C]
cmp     eax, [ebp+var_1C]
jnz      short loc_40151B


to

loc_4014FD:
mov     eax, [ebp+var_C]
cmp     eax, [ebp+var_1C]
jz      short loc_40151B