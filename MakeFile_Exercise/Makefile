#Some defitions here:
CC := g++
CXXFLAGS := -std=c++17
QUIET := @
ECHO := echo
RM := rm
INSTALL_DIR ?= installation_prefix

SOURCES := main.cpp utilites_floats.cpp utilites_ints.cpp
OBJECTS := $(SOURCES:.cpp=.o)
#$(info "SOURCES = $(SOURCES) , but OBJECTS = $(OBJECTS)")

# $@ is the name of file being created by the rule.
# $^ is the list of dependencies.

math_app: $(OBJECTS)
	$(QUIET)$(ECHO) "building math_app!"
	$(QUIET)$(CC) -o $@ $^

# https://www.gnu.org/software/make/manual/html_node/Automatic-Variables.html
%.o: %.cpp
	$(QUIET)$(ECHO) "compiling $< ..."
	$(QUIET)$(CC) $(CXXFLAGS) -o "$@" -c $<

install_dir:
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then mkdir "$(INSTALL_DIR)" ; fi
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then echo "$(INSTALL_DIR) is not created" ; exit 1 ; fi

install: install_dir
	install -m 755 app "$(INSTALL_DIR)/math_app"

default: math_app

.PHONY: clean distclean install_dir

distclean: clean
	$(QUIET)$(ECHO) "removing app....!"
	$(QUIET)$(RM) -f $(BUILD_DIR)/math_app

clean:
	$(QUIET)$(ECHO) "removing all object files!"
	$(QUIET)$(RM) -f $(OBJECTS)/*.o