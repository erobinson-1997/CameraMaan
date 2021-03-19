##################################################
# PROJECT: Dynamixel servo startup dance.
# AUTHOR : Ethan Robinson
##################################################

TARGET      = CameraMaan

# important directories used by assorted rules and other variables
DIR_DXL    = /usr/local
DIR_OBJS   = .objects

#---------------------------- Compiler Options --------------------------------
CC          = gcc
CX          = g++
CCFLAGS     = -O2 -O3 -DLINUX -D_GNU_SOURCE -Wall $(INCLUDES) $(FORMAT) -g
CXFLAGS     = -O2 -O3 -DLINUX -D_GNU_SOURCE -Wall $(INCLUDES) $(FORMAT) -g
LNKCC       = $(CX)
LNKFLAGS    = $(CXFLAGS) #-Wl,-rpath,$(DIR_THOR)/lib
FORMAT      = 

#----------------------------- Core Components --------------------------------
# Core components 
INCLUDES   += -I$(DIR_DXL)/include/dynamixel_sdk 
INCLUDES   += -I$(DIR_DXL)/include/opencv4
LIBRARIES  += -ldxl_x64_cpp
LIBRARIES  += -lrt
LIBRARIES  += -pthread
LIBRARIES  += -L/usr/local/lib -lopencv_core -lopencv_flann -lopencv_video

#------------------------------ Files -----------------------------------------

SOURCES = CameraMaan.cpp \
	  dxl_servo_controller.cpp
    # *** OTHER SOURCES GO HERE ***

OBJECTS  = $(addsuffix .o,$(addprefix $(DIR_OBJS)/,$(basename $(notdir $(SOURCES)))))
OBJETCS += $(addprefix $(DIR_OBJS)/, dxl_servo_controller.o)


#------------------------- Compiling Rules ------------------------------------

$(TARGET): make_directory $(OBJECTS)
	$(LNKCC) $(LNKFLAGS) $(OBJECTS) -o $(TARGET) `pkg-config --libs opencv4` $(LIBRARIES)

all: $(TARGET)

clean:
	rm -rf $(TARGET) $(DIR_OBJS) core *~ *.a *.so *.lo

make_directory:
	mkdir -p $(DIR_OBJS)/

$(DIR_OBJS)/%.o: ../%.c
	$(CC) $(CCFLAGS) -c $? -o $@

$(DIR_OBJS)/%.o: ../%.cpp
	$(CX) $(CXFLAGS) -c $? -o $@

