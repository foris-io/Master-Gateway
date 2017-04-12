include radio.makefile

lora_gateway: lora_gateway.o arduPi.o SX1272.o
	g++ -lrt -lpthread lora_gateway.o arduPi.o SX1272.o -o lora_gateway -lcurl	

lora_gateway_pi2: lora_gateway_pi2.o arduPi_pi2.o SX1272_pi2.o
	g++ -lrt -lpthread lora_gateway_pi2.o arduPi_pi2.o SX1272_pi2.o -o lora_gateway_pi2 -lcurl
	rm -f lora_gateway
	ln -s lora_gateway_pi2 ./lora_gateway
		
lora_gateway_wnetkey: lora_gateway.o arduPi.o SX1272_wnetkey.o
	g++ -lrt -lpthread lora_gateway.o arduPi.o SX1272_wnetkey.o -o lora_gateway_wnetkey -lcurl	

lora_gateway_pi2_wnetkey: lora_gateway_pi2.o arduPi_pi2.o SX1272_pi2_wnetkey.o
	g++ -lrt -lpthread lora_gateway_pi2.o arduPi_pi2.o SX1272_pi2_wnetkey.o -o lora_gateway_pi2_wnetkey -lcurl

lora_gateway_winput: lora_gateway_winput.o arduPi.o SX1272.o
	g++ -lrt -lpthread lora_gateway_winput.o arduPi.o SX1272.o -o lora_gateway_winput -lcurl

lora_gateway_pi2_winput: lora_gateway_pi2_winput.o arduPi_pi2.o SX1272_pi2.o
	g++ -lrt -lpthread lora_gateway_pi2_winput.o arduPi_pi2.o SX1272_pi2.o -o lora_gateway_pi2_winput -lcurl

lora_gateway.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DIS_RCV_GATEWAY -c lora_gateway.cpp -o lora_gateway.o -lcurl

lora_gateway_pi2.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DRASPBERRY2 -DIS_RCV_GATEWAY -c lora_gateway.cpp -o lora_gateway_pi2.o -lcurl

lora_gateway_winput.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DIS_RCV_GATEWAY -DWINPUT -c lora_gateway.cpp -o lora_gateway_winput.o -lcurl

lora_gateway_pi2_winput.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DRASPBERRY2 -DIS_RCV_GATEWAY -DWINPUT -c lora_gateway.cpp -o lora_gateway_pi2_winput.o -lcurl

arduPi.o: arduPi.cpp arduPi.h
	g++ -c arduPi.cpp -o arduPi.o -lcurl	

arduPi_pi2.o: arduPi_pi2.cpp arduPi_pi2.h
	g++ -c arduPi_pi2.cpp -o arduPi_pi2.o -lcurl	

SX1272.o: SX1272.cpp SX1272.h
	g++ -c SX1272.cpp -o SX1272.o -lcurl

SX1272_pi2.o: SX1272.cpp SX1272.h
	g++ -DRASPBERRY2 -c SX1272.cpp -o SX1272_pi2.o -lcurl

SX1272_wnetkey.o: SX1272.cpp
	g++ -DW_NET_KEY -c SX1272.cpp -o SX1272_wnetkey.o -lcurl

SX1272_pi2_wnetkey.o: SX1272.cpp
	g++ -DRASPBERRY2 -DW_NET_KEY -c SX1272.cpp -o SX1272_pi2_wnetkey.o -lcurl

lora_las_gateway: lora_las_gateway.o LoRaActivitySharing.o arduPi.o SX1272.o
	g++ -lrt -lpthread lora_las_gateway.o LoRaActivitySharing.o arduPi.o SX1272.o -o lora_las_gateway -lcurl

lora_las_gateway_pi2: lora_las_gateway_pi2.o LoRaActivitySharing.o arduPi_pi2.o SX1272_pi2.o
	g++ -lrt -lpthread lora_las_gateway_pi2.o LoRaActivitySharing.o arduPi_pi2.o SX1272_pi2.o -o lora_las_gateway_pi2 -lcurl

lora_las_gateway_wnetkey: lora_las_gateway.o LoRaActivitySharing.o arduPi.o SX1272_wnetkey.o
	g++ -lrt -lpthread lora_las_gateway.o LoRaActivitySharing.o arduPi.o SX1272_wnetkey.o -o lora_las_gateway_wnetkey -lcurl

lora_las_gateway_pi2_wnetkey: lora_las_gateway_pi2.o LoRaActivitySharing.o arduPi_pi2.o SX1272_pi2_wnetkey.o
	g++ -lrt -lpthread lora_las_gateway.o LoRaActivitySharing.o arduPi_pi2.o SX1272_pi2_wnetkey.o -o lora_las_gateway_pi2_wnetkey -lcurl
	
lora_las_gateway.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DIS_RCV_GATEWAY -DLORA_LAS -c lora_gateway.cpp -o lora_las_gateway.o -lcurl

lora_las_gateway_pi2.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DRASPBERRY2 -DIS_RCV_GATEWAY -DLORA_LAS -c lora_gateway.cpp -o lora_las_gateway_pi2.o -lcurl

LoRaActivitySharing.o: LoRaActivitySharing.cpp LoRaActivitySharing.h
	g++ -c LoRaActivitySharing.cpp -o LoRaActivitySharing.o -lcurl

#for testing as a very simple end-device
lora_device: lora_gateway_dev.o arduPi.o SX1272.o
	g++ -lrt -lpthread lora_gateway_dev.o arduPi.o SX1272.o -o lora_device -lcurl	

lora_device_pi2: lora_gateway_dev_pi2.o arduPi_pi2.o SX1272_pi2.o
	g++ -lrt -lpthread lora_gateway_dev.o arduPi_pi2.o SX1272_pi2.o -o lora_device_pi2 -lcurl

lora_gateway_dev.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DIS_SEND_GATEWAY -DWINPUT -c lora_gateway.cpp -o lora_gateway_dev.o -lcurl

lora_gateway_dev_pi2.o: lora_gateway.cpp
	g++ $(CFLAGS) -DRASPBERRY -DRASPBERRY2 -DIS_SEND_GATEWAY -DWINPUT -c lora_gateway.cpp -o lora_gateway_dev_pi2.o -lcurl
all:
	-@mkdir -p bin
	gcc main.c -lcurl -o bin/main

#end
		
lib: arduPi.o arduPi_pi2.o SX1272.o SX1272_pi2.o SX1272_wnetkey.o SX1272_pi2_wnetkey.o lora_gateway.o lora_las_gateway.o lora_gateway_pi2.o lora_las_gateway_pi2.o

clean:
	-rm *.o lora_*gateway
