obj-m += create_device_file.o
 
KDIR = /lib/modules/$(shell uname -r)/build

 
all:
	rm -rf build
	make -C $(KDIR)  M=$(shell pwd) modules
	mkdir build
	mv *.o *.mod.c *.ko .* *.mod *.order *.symvers build/ 
 
clean:
	make -C $(KDIR)  M=$(shell pwd) clean