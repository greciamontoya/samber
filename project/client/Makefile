# Makefile
# Ejemplo  Server en Raspberry Pi
# Precaucion: Debe seguir los pasos que se indicaron a pie de la letra
# https://github.com/cidte/samber

CC            = g++
CFLAGS        = -DRASPBERRY_PI -DBCM2835_NO_DELAY_COMPATIBILITY -D__BASEFILE__=\"$*\" `mysql_config --cflags` 
LIBS          = -lbcm2835 `mysql_config --libs ` -lwiringPi
RADIOHEADBASE = ../../
INCLUDE       = -I$(RADIOHEADBASE)

all: rf95_client

RasPi.o: $(RADIOHEADBASE)/RHutil/RasPi.cpp
				$(CC) $(CFLAGS) -c $(RADIOHEADBASE)/RHutil/RasPi.cpp $(INCLUDE)

rf95_client.o: rf95_client.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RH_RF95.o: $(RADIOHEADBASE)/RH_RF95.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHDatagram.o: $(RADIOHEADBASE)/RHDatagram.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHHardwareSPI.o: $(RADIOHEADBASE)/RHHardwareSPI.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHSPIDriver.o: $(RADIOHEADBASE)/RHSPIDriver.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHGenericDriver.o: $(RADIOHEADBASE)/RHGenericDriver.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<

RHGenericSPI.o: $(RADIOHEADBASE)/RHGenericSPI.cpp
				$(CC) $(CFLAGS) -c $(INCLUDE) $<


rf95_client: rf95_client.o RH_RF95.o RasPi.o RHHardwareSPI.o RHGenericDriver.o RHGenericSPI.o RHSPIDriver.o
				$(CC) $^ $(LIBS) -o rf95_client

clean:
				rm -rf *.o  rf95_cliet
