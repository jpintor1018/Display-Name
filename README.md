
.model	large

.stack 32

.data
MSG		DB		"Enter Your Name: ",'$'
MSG2		DB		"Enter Your Address: ",'$'
KBinput DB		10 DUP('  '),'$'
KBinput2 DB		50 DUP('  '),'$'
prompt 	DB		"Your Name Is: ",0DH,0AH,'$'
prompt2	DB		"Your Address is: ",0DH,0AH,'$'

.code

MAIN PROC FAR

MOV AX, @DATA
MOV DS,AX

LEA DX, MSG
MOV AH, 09H
INT 21H

MOV AH, 03FH ; KBinput
MOV BX, 00
MOV CX, 10 
LEA DX, KBinput
INT 21H

LEA DX, MSG2
MOV AH, 09H
INT 21H

MOV AH, 03FH ; KBinput2
MOV BX,00
MOV CX,50
LEA DX, KBinput2
INT 21H

LEA DX, prompt
MOV AH, 09H
INT 21H

LEA DX, KBinput
MOV AH, 09H
INT 21H

LEA DX, prompt2
MOV AH, 09H
INT 21H

LEA DX, KBinput2
MOV AH, 09H
INT 21H

MOV AX,4C00H
INT 21H

MAIN ENDP
END MAIN


