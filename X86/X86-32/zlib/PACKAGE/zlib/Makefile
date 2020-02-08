first_rule: all

all: build

PACKAGE_NAME := zlib-1.2.11
PACKAGE_DIR  := zlib-1.2.11

# Configuration
PACKAGE_CONF := \
    --prefix=$(CURDIR)/../../OBJ/ \

Compile386 := \
        CC="gcc -m32" \

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
	cd $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/  && $(Compile386) ./configure  $(PACKAGE_CONF); \

build: build_lib install
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ all

install:
	$(MAKE) -C $(CURDIR)/../../TARGET/$(PACKAGE_DIR)/ install
	
config_rule:

clean_rule:

uninstall_rule:
