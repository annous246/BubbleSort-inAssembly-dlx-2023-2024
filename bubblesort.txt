.data 0x1000

; ArrayList:

.global a
a: .word 45,45,8,7,1,1,5,1,7,7 
.global s
s: .word 0
.text
main:
loop1:
add r11,r0,r0
add r11,r11,a
add r24,r0,r0
add r24,r24,a
addi r22,r22,#9 ; Length of ArrayList - 1 (for sorting and comparing purposes) 
add r4,r0,r0
addi r5,r0,#0
loop2:
lw r1,0(r11)
addi r11,r11,#4
lw r2,0(r11)
subi r22,r22,#1
slt r4,r2,r1
add r5,r5,r4
beqz r4,j
sw 0(r24),r2
sw 0(r11),r1
j:
addi r24,r24,#4

bnez r22,loop2
bnez r5,loop1

trap 0