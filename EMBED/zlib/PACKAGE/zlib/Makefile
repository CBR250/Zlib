first_rule: all

all: build

PACKAGE_NAME := zlib-1.2.11
PACKAGE_DIR  := zlib-1.2.11

PATH := /opt/toolchains/crosstools-arm-gcc-5.5-linux-4.1-glibc-2.26-binutils-2.28.1/bin:$(PATH)

# Configuration
PACKAGE_CONF := \
    --prefix=$(CURDIR)/../../OBJ/ \

CrossCompile := \
        CC=arm-buildroot-linux-gnueabi-gcc \
        AR=arm-buildroot-linux-gnueabi-ar \
        CPP=arm-buildroot-linux-gnueabi-g++ \

test_directory:
	if [ ! -d $(CURDIR)/../../TARGET ]; then \
	   mkdir $(CURDIR)/../../TARGET/; \
	fi
	if [ -d $(CURDIR)/../../TARGET/$(PACKAGE_DIR) ]; then \
	       echo "Folder existed"; \
	else \
	       tar xvf $(CURDIR)/$(PACKAGE_NAME).tar.gz -C $(CURDIR)/../../TARGET/; \
	fi

build_lib: test_directory
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/  && $(CrossCompile) ./configure  $(PACKAGE_CONF); \

build: build_lib install
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ all

install:
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ install
	
config_rule:

clean_rule:

uninstall_rule:
