### Output:
TARGET = sproxie
OBJECT_DIR = obj/
BUILD_DIR = bin/

### Input:
#SOURCE - Input folders to compile
SOURCE := . HTTPClient
#SOURCE_DIR - Root folder for the source code relative to Makefile
SOURCE_DIR = src/

### Buildtools:
COMPILER = clang
LINKER = gcc
COMPILE_FLAGS = -Wall #-std=c99
LINK_FLAGS = -lpthread


### Build:

SRC_DIR := $(addprefix $(SOURCE_DIR), $(SOURCE))
SRC_COMPILE := $(foreach sdir, $(SRC_DIR), $(wildcard $(sdir)/*.c))
SRC_OBJECTS := $(patsubst $(SOURCE_DIR)%.c, $(OBJECT_DIR)%.o, $(SRC_COMPILE))

all: clean $(TARGET)

clean:
	rm -rf $(BUILD_DIR)
	rm -rf $(OBJECT_DIR)

$(SRC_OBJECTS): $(OBJECT_DIR)
	@mkdir -p $(@D)
	$(COMPILER) $(COMPILE_FLAGS) -c $(patsubst $(OBJECT_DIR)%.o, $(SOURCE_DIR)%.c, $@) -o $(patsubst .$(@D)%.o, $(OBJECT_DIR)%.o, $@)

$(TARGET): $(SRC_OBJECTS) $(BUILD_DIR)
	$(LINKER) $(SRC_OBJECTS) -o $(BUILD_DIR)$(TARGET) $(LINK_FLAGS)

$(OBJECT_DIR):
	mkdir $@

$(BUILD_DIR):
	mkdir $@
