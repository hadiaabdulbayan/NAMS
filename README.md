section .data
    msg db 'Hi!', 0

section .text
    global _start

_start:
    ; Write msg to stdout
    mov eax, 4          ; syscall: write
    mov ebx, 1          ; file descriptor: stdout
    mov ecx, msg        ; pointer to msg
    mov edx, 3          ; length of msg
    int 0x80            ; call kernel

    ; Exit
    mov eax, 1          ; syscall: exit
    xor ebx, ebx        ; exit code 0
    int 0x80            ; call kernel
