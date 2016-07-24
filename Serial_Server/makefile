######################################################################
#
# Project:     XTIDE Universal BIOS, Serial Port Server
#
# File:        makefile
#
# Use with GNU Make
#

BUILD_DIR = build
HEADERS = library/Library.h linux/LinuxFile.h linux/LinuxSerial.h library/File.h library/FlatImage.h

CXX = c++
CXXFLAGS = -g 

LINUXOBJS = $(BUILD_DIR)/linux.o $(BUILD_DIR)/checksum.o $(BUILD_DIR)/serial.o $(BUILD_DIR)/process.o $(BUILD_DIR)/image.o

all: build_dir $(BUILD_DIR)/serdrive

build_dir:
	mkdir -p $(BUILD_DIR)

$(BUILD_DIR)/serdrive:	$(LINUXOBJS)
	$(CXX) -lrt -o $(BUILD_DIR)/serdrive $(LINUXOBJS)

$(BUILD_DIR)/linux.o:	linux/Linux.cpp $(HEADERS)
	$(CXX) -c $(CXXFLAGS) linux/Linux.cpp -o $(BUILD_DIR)/linux.o

$(BUILD_DIR)/checksum.o:	library/Checksum.cpp $(HEADERS)
	$(CXX) -c $(CXXFLAGS) library/Checksum.cpp -o $(BUILD_DIR)/checksum.o

$(BUILD_DIR)/serial.o:	library/Serial.cpp $(HEADERS)
	$(CXX) -c $(CXXFLAGS) library/Serial.cpp -o $(BUILD_DIR)/serial.o

$(BUILD_DIR)/process.o:	library/Process.cpp $(HEADERS)
	$(CXX) -c $(CXXFLAGS) library/Process.cpp -o $(BUILD_DIR)/process.o

$(BUILD_DIR)/image.o:	library/Image.cpp $(HEADERS)
	$(CXX) -c $(CXXFLAGS) library/Image.cpp -o $(BUILD_DIR)/image.o


clean:
	rm -rf build


$(BUILD_DIR)/checksum_test.exe:	library/checksum.cpp
	$(CXX) /Fe$(BUILD_DIR)/checksum_test.exe /Ox library/checksum.cpp /Fo$(BUILD_DIR)/checksum_test.obj -D CHECKSUM_TEST

