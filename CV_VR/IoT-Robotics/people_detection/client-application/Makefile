# Define toolchains
CC_x86 := gcc
CC_aarch64 := aarch64-linux-gnu-gcc

# Define flags
CFLAGS_x86 := -m64
CFLAGS_aarch64 :=

# Define build directories
BUILD_DIR_x86 := ./build_x86
BUILD_DIR_aarch64 := ./build_aarch64

# Define source directories
SRC_DIRS := ./src

# Find source files
SRCS := $(shell find $(SRC_DIRS) -name *.c -or -name *.s)

# Define object files
OBJS_x86 := $(SRCS:%=$(BUILD_DIR_x86)/%.o)
OBJS_aarch64 := $(SRCS:%=$(BUILD_DIR_aarch64)/%.o)

# Define targets
TARGET_x86 := $(BUILD_DIR_x86)/socket_client_x86
TARGET_aarch64 := $(BUILD_DIR_aarch64)/socket_client_aarch64

# Include directories
INC_DIRS := $(shell find $(SRC_DIRS) -type d)
INC_FLAGS := $(addprefix -I,$(INC_DIRS))

# Compilation flags
CPPFLAGS := $(INC_FLAGS) -MMD -MP

# Build rules
all: $(TARGET_x86) $(TARGET_aarch64)

$(TARGET_x86): $(OBJS_x86)
	$(CC_x86) $(OBJS_x86) -o $@ $(LDFLAGS)

$(TARGET_aarch64): $(OBJS_aarch64)
	$(CC_aarch64) $(OBJS_aarch64) -o $@ $(LDFLAGS)

# Rules for compiling source files
$(BUILD_DIR_x86)/%.c.o: %.c
	$(MKDIR_P) $(dir $@)
	$(CC_x86) $(CPPFLAGS) $(CFLAGS_x86) -c $< -o $@

$(BUILD_DIR_aarch64)/%.c.o: %.c
	$(MKDIR_P) $(dir $@)
	$(CC_aarch64) $(CPPFLAGS) $(CFLAGS_aarch64) -c $< -o $@

.PHONY: clean

clean:
	$(RM) -r $(BUILD_DIR_x86)
	$(RM) -r $(BUILD_DIR_aarch64)

MKDIR_P ?= mkdir -p
