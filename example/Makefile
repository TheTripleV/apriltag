CC = arm-frc2022-linux-gnueabi-gcc
CXX = arm-frc2022-linux-gnueabi-g++

CPPFLAGS = -I.. `pkg-config --cflags opencv4`
CFLAGS = -g -std=gnu99 -Wall -Wno-unused-parameter -Wno-unused-function -O2
CXXFLAGS = -g -Wall -O2
LDFLAGS = -lpthread -lm

TARGETS := apriltag_demo opencv_demo

.PHONY: all
all: apriltag_demo opencv_demo

apriltag_demo: apriltag_demo.o ../libapriltag.a
	@echo "   [$@]"
	@$(CC) -o $@ $^ $(LDFLAGS)

opencv_demo: opencv_demo.o ../libapriltag.a
	@echo "   [$@]"
	@$(CXX) -o $@ $^ $(LDFLAGS) `pkg-config --libs opencv4`

%.o: %.c
	@echo "   $@"
	@$(CC) -o $@ -c $< $(CFLAGS) $(CPPFLAGS)

%.o: %.cc
	@echo "   $@"
	@$(CXX) -o $@ -c $< $(CXXFLAGS) $(CPPFLAGS)

.PHONY: clean
clean:
	@rm -rf *.o $(TARGETS)
