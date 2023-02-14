#Some defitions here:
CXX := g++
CXXFLAGS := -std=c++17
QUIET := @
ECHO := echo
RM := rm
INSTALL_DIR ?= installation_prefix
BUILD_DIR := .
AUTOCLEAN := $(QUIET)$(RM) -f $(BUILD_DIR)/*.o
APPNAME := körv_app

SOURCES := main.cpp utilites_floats.cpp utilites_ints.cpp
OBJECTS := $(SOURCES:.cpp=.o)

# $@ is the name of file being created by the rule.
# $^ is the list of dependencies.

$(APPNAME): $(OBJECTS)
	$(QUIET)$(ECHO) "building $(APPNAME)!"
	$(QUIET)$(CXX) -o $@ $^
	$(QUIET)$(ECHO) "Hello my name is körv! I will remove the objectfiles for you!! mohahaha!"
	$(QUIET)$(AUTOCLEAN)


# https://www.gnu.org/software/make/manual/html_node/Automatic-Variables.html
%.o: %.cpp 
	$(QUIET)$(ECHO) "compiling $< ..."
	$(QUIET)$(CXX) $(CXXFLAGS) -o "$@" -c $<

install_dir:
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then mkdir "$(INSTALL_DIR)" ; fi
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then echo "$(INSTALL_DIR) is not created" ; exit 1 ; fi

install: install_dir
	install -m 755 $(APPNAME) "$(INSTALL_DIR)/$(APPNAME)"

default: app


.PHONY: clean distclean install_dir


distclean: clean
	$(QUIET)$(ECHO) "removing app....!"
	$(QUIET)$(RM) -f $(BUILD_DIR)/$(APPNAME)

clean:
	$(QUIET)$(ECHO) "removing all object files!"
	$(QUIET)$(RM) -f $(BUILD_DIR)/*.o

