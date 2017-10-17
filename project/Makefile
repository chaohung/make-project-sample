SRC_DIR = ../src

OBJ_DIR = ./build/objs

MODULES = core util

SRC_SUBDIRS = $(addprefix $(SRC_DIR)/, $(MODULES))

SRCS = $(foreach sdir, $(SRC_SUBDIRS), $(wildcard $(sdir)/*.cpp))

BUILD_DIRS = $(addprefix $(OBJ_DIR)/, $(MODULES))

OBJS = $(subst $(SRC_DIR), $(OBJ_DIR), $(SRCS:.cpp=.o))

DEPS = $(OBJS:.o=.d)

TARGET = ./build/main

INCLUDE_DIR =\
-I$(SRC_DIR)\

LIB_DIR =

CXX = g++

CXXFLAGS = -std=c++11

LDFLAGS =

all: $(TARGET)

-include $(DEPS)

$(TARGET) : $(BUILD_DIRS) $(OBJS) ./main.cpp
	$(CXX) $(CXXFLAGS) $(INCLUDE_DIR) -o $@ $(OBJS) $(LIB_DIR) $(LDFLAGS) ./main.cpp

$(OBJ_DIR)/%.o : $(SRC_DIR)/%.cpp 
	$(CXX) $(CXXFLAGS) $(INCLUDE_DIR) -c -MMD $< -o $@

$(BUILD_DIRS):
	mkdir -p $@

clean:
	$(RM) $(OBJS) $(DEPS)

.PHONY: all clean
