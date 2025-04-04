# Turning it on

1. gcc -m32 -ffreestanding -nostartfiles -c src/kernel.c -o objs/kernel.o
2. gcc -m32 -ffreestanding -nostartfiles -c src/idt.c -o objs/idt.o
3. gcc -m32 -ffreestanding -nostartfiles -c src/keyboard.c -o objs/keyboard.o
4. gcc -m32 -ffreestanding -nostartfiles -c src/video.c -o objs/video.o
5. nasm -f elf32 src/idt_flush.s -o objs/idt_flush.o
6. nasm -f elf32 src/keyboard_stub.s -o objs/keyboard_stub.o
7. ld -m elf_i386 -T undefined/linker.ld -o iso/boot/kernel.elf objs/*.o
8. grub-mkrescue -o myos.iso iso/boot/ 
9. qemu-system-i386 -drive format=raw,file=myos.iso (INIT)

# Recompile the changed files before initialization. (!!!)

When you're already in the GNU, you can type "ls".
The first one to appear (in this case it's "(hd0)") has the kernel.elf file inside.
To finally boot, you have to type:

1. multiboot (hd0)/kernel.elf    ///// OR ///// multiboot (cd)/kernel.elf (IT IS BASED ON HOW YOU TURN QEMU ON)
2. boot

At this point you already booted your kernel.

# 
