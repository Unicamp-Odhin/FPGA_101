all:
	quartus_sh --flow compile de1soc
	
load:
	quartus_pgm -m jtag -c "DE-SoC " -o "p;build/de1soc.sof@2"

clean:
	rm -rf build/*
	rm -rf .env
	rm -rf output_files/*
	rm -rf db/*
	rm -rf *.o
	rm -rf *.vcd


buildFolder:
	mkdir -p build
