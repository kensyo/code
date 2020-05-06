# compile command
CC		:= g++

# compile options (debug)
DEBUG_CFLAGS	:= -Wall -g -std=c++17

# compile options (release)
RELEASE_CFLAGS	:= -Wall -O2 -std=c++17 -DNDEBUG

# link options
LFLAGS 	:= -lSDL2 -lSDL2_image -lpng16 -llua -lGL -lGLEW -lglfw -lXi -lXrandr -lXxf86vm -lX11 -lrt -lm -lSOIL

# made execution file (debug)
DEBUG_TARGET 	:= debug.out

# made execution file (release)
RELEASE_TARGET 	:= release.out

# fmodstudioapi directory
FMOD := fmodstudioapi10921linux

# include directory
INCLUDE := 

# static(*.a) or shared(*.so) library directory
LIB 	:= 

# the name of debug directory
DEBUG_DIR := Debug

# the name of release directory
RELEASE_DIR := Release

# main directory of the generated object files
OBJ_DIR	:= build

# source directory
SRC_DIR	:= .

# no make dirctories(with %) or files
NO_MAKE_PATH := 

# exceptional sources(which are compiled)
EXEPTIONAL_SOURCES := #library/lib/lodepng/lodepng.cpp

# souce files
SOURCES := $(shell find $(SRC_DIR) -name '*.cpp' -print)

# filtered source files
FILTERED_SOURCES := $(filter-out $(NO_MAKE_PATH), $(SOURCES))

# all the sources
ALL_SOURCES := $(FILTERED_SOURCES) $(EXEPTIONAL_SOURCES)

# generated object files
OBJECTS := $(ALL_SOURCES:.cpp=.o)

# dirctories of all the objects
ALL_OBJECTS_DIRECTORIES := $(dir $(OBJECTS))

# full path of the objects for Debug, and that for Release
DEBUG_OBJECTS := $(addprefix $(OBJ_DIR)/$(DEBUG_DIR)/, $(OBJECTS))
RELEASE_OBJECTS := $(addprefix $(OBJ_DIR)/$(RELEASE_DIR)/, $(OBJECTS))

# main file
MAIN_FILE := ./Main.cpp

# dependencies(*.d files)
DEBUG_DEPENDENCIES := $(DEBUG_OBJECTS:.o=.d)
RELEASE_DEPENDENCIES := $(RELEASE_OBJECTS:.o=.d)

.PHONY: debug release clean run run_debug run_release

debug: CFLAGS := $(DEBUG_CFLAGS)
debug: $(DEBUG_TARGET);

release: CFLAGS := $(RELEASE_CFLAGS)
release: $(RELEASE_TARGET);

$(DEBUG_TARGET): $(DEBUG_OBJECTS)
	$(CC) -o $@ $(DEBUG_OBJECTS) $(LIB) $(LFLAGS)

$(RELEASE_TARGET): $(RELEASE_OBJECTS)
	$(CC) -o $@ $(RELEASE_OBJECTS) $(LIB) $(LFLAGS) 

$(OBJ_DIR)/$(DEBUG_DIR)/%.o $(OBJ_DIR)/$(RELEASE_DIR)/%.o: %.cpp
	@if [ ! -d $(dir $@) ] ; then \
	    echo "mkdir -p $(dir $@)" && mkdir -p $(dir $@) ; \
	fi
	$(CC) $(INCLUDE) -MD -MP -o $@ -c $< $(CFLAGS)

clean:
	rm -rf $(OBJ_DIR) $(DEBUG_TARGET) $(RELEASE_TARGET) $(LIBRARY_TARGET)

run: run_debug;

run_debug: debug
	./$(DEBUG_TARGET)

run_release: release
	./$(RELEASE_TARGET)

-include $(DEBUG_DEPENDENCIES) $(RELEASE_DEPENDENCIES) 

