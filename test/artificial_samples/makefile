CC_x64=gcc
CC_X86=gcc
CC_ARM=arm-linux-gnueabi-gcc-7
CC_MIPS=mips-linux-gnu-gcc-7
CC_PPC=powerpc-linux-gnu-gcc-7

CFLAGS_X64=-O0 -g -fno-stack-protector
CFLAGS_X86=-O0 -g -m32 -fno-stack-protector
CFLAGS_ARM=-O0 -g -fno-stack-protector 
CFLAGS_MIPS=-O0 -g -fno-stack-protector
CFLAGS_PPC=-O0 -g -fno-stack-protector

define compile_x64
	@echo "Compiling x64 target:" $(1)
	$(CC_x64) $(CFLAGS_X64) -o build/$(1)_x64.out $(1).c
	execstack -s build/$(1)_x64.out
endef

define compile_x86
	@echo "Compiling x86 target:" $(1)
	$(CC_X86) $(CFLAGS_X86) -o build/$(1)_x86.out $(1).c
	execstack -s build/$(1)_x86.out
endef

define compile_mips
	@echo "Compiling mips target:" $(1)
	$(CC_MIPS) $(CFLAGS_MIPS) -o build/$(1)_mips.out $(1).c
	execstack -s build/$(1)_mips.out
endef

define compile_arm
	@echo "Compiling arm target:" $(1)
	$(CC_ARM) $(CFLAGS_ARM) -o build/$(1)_arm.out $(1).c
	execstack -s build/$(1)_arm.out
endef

define compile_ppc
	@echo "Compiling ppc target:" $(1)
	$(CC_PPC) $(CFLAGS_PPC) -o build/$(1)_ppc.out $(1).c
	execstack -s build/$(1)_ppc.out
endef

define compile_all
	$(shell mkdir -p "build")
	$(call compile_x64,$(1))
	$(call compile_x86,$(1))
	$(call compile_arm,$(1))
	$(call compile_mips,$(1))
	$(call compile_ppc,$(1))
endef

all:
	$(call compile_all,c_constructs)
	$(call compile_all,cwe_190)
	$(call compile_all,cwe_243)
	$(call compile_all,cwe_243_clean)
	$(call compile_all,cwe_332)
	$(call compile_all,cwe_367)
	$(call compile_all,cwe_415)
	$(call compile_all,cwe_426)
	$(call compile_all,cwe_457)			
	$(call compile_all,cwe_467)
	$(call compile_all,cwe_476)
	$(call compile_all,cwe_478)
	$(call compile_x64,cwe_782)	
	$(call compile_all,arrays)
	$(call compile_all,memory_access)	

clean:
	rm -rf build

