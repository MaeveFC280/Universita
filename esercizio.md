
| A   | B   | C   | Output |
| --- | --- | --- | ------ |
| 0   | 0   | X   | 0      |
| 0   | 1   | 0   | 0      |
| 0   | 1   | 1   | 1      |
| 1   | 0   | 0   | 1      |
| 1   | 0   | 1   | 0      |
| 1   | 1   | X   | 1      |
OUTPUT= BC + NOT B NOT C A + AB

CONTA CHE: Sto facendo tutto da computer quindi potrei aver confuso: formua sop perchè non posso disegnare karnaugh, l'ordine di 0 e 1 nei primi esercizi 
``` C
int x=10;
int y = 2;

while(x>=0){
	x=x-y;
	y++;
}
y+=3;

```

void modifica(int *p) {
    if (*p >= 4) {
        *p = *p + 2;
    }
    else {
        p = p + 1;
    }
}
```
PUSH(R1)
LDR R1 [R0]
CMP R1 #4
BLT ELSE
ADD R1 R1 #2
STR R1 [R0]
B END
ELSE
ADD R0 R0 #4
END
POP(R1)
```
