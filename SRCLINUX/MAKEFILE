IMAGE_OFFSET = 0x94010

KDIR = /usr/src/linux
HEAD = loadlinh.o
SYS_SIZE = -DSYS_SIZE=0xFFFF

OBJECTS = $(HEAD) pgadjust.o

CFLAGS = -D__KERNEL__ -m386 -O2 -DSTDC_HEADERS -fomit-frame-pointer \
         -fno-strength-reduce -fno-force-mem

ifneq (1,$(shell if grep __ELF__ `gcc -v 2>&1|head -n1|cut -d' ' -f4` 1>/dev/null 2>&1;then echo -n 1;fi))
  @echo ""; \
   echo "needing ELF development tools, giving up";
  exit 1;
endif

all: pgadjust.asm Makefile
#all: testpg Makefile

pgadjust.asm: pgadjust.out Makefile
	echo "; 32-bit code, linkaddress: $(IMAGE_OFFSET)" >pgadjust.as
	hexdump -v -e '" DD  " 8/4 "0%Xh," 1/4 "0%Xh\n"' pgadjust.out >>pgadjust.as
	todos <pgadjust.as >pgadjust.asm
	rm -f pgadjust.as

pgadjust.out: pgadjust Makefile
	objdump -k -q  -o $(IMAGE_OFFSET) pgadjust > pgadjust.out
	
loadlinh.o: loadlinh.S
	$(CC) -traditional -c loadlinh.S

pgadjust: $(OBJECTS) Makefile
	ld -m elf_i386 -Ttext $(IMAGE_OFFSET) -relax -e startup_32  -o pgadjust $(OBJECTS)
#                      this avoids page align ^^^^^^ (and holes between sections)

pgadjust.o: pgadjust.c
	$(CC) $(CFLAGS) -c pgadjust.c -o pgadjust.o

testpg: pgadjust.c
	$(CC) $(CFLAGS) -DSTANDALONE_DEBUG -o testpg pgadjust.c

clean:
	rm -f $(OBJECTS) pgadjust.asm pgadjust.out pgadjust
