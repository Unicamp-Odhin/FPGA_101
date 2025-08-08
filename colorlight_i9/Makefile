.PHONY: all load

all: build/out.bit

build/out.bit: build/out.config
	ecppack --compress --input build/out.config --bit build/out.bit

build/out.config: build/out.json pinout.lpf
	nextpnr-ecp5 --json build/out.json --lpf build/pinout.lpf --textcfg build/out.config \
	--package CABGA381 --45k --speed 6 --lpf-allow-unconstrained

build/out.json: main.sv buildFolder
	yosys -p "read_verilog -sv main.sv; \
		synth_ecp5 -json build/out.json -abc9"

load: build/out.bit
	openFPGALoader -b colorlight-i9 build/out.bit

buildFolder:
	mkdir -p build

clean:
	rm -f build/