PROJECT=3_Motion_Control_Simple
SOURCES=$(PROJECT).c
MMCU=atmega2560

CFLAGS=-mmcu=$(MMCU) -Wall -Os -DF_CPU=14745600

$(PROJECT).hex: $(PROJECT).out
	avr-objcopy -O ihex $(PROJECT).out $(PROJECT).hex;\
	avr-size --mcu=$(MMCU) --format=avr $(PROJECT).out
 
$(PROJECT).out: $(SOURCES)
	avr-gcc $(CFLAGS) -I./ -o $(PROJECT).out $(SOURCES)
 
flash:
	avrdude -c avrispv2 -p m2560 -P /dev/ttyACM4 -U flash:w:$(PROJECT).hex
