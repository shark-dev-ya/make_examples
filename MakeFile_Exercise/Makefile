#Some defitions here:
CC := g++
CXXFLAGS := -std=c++17
QUIET := @
ECHO := echo
RM := rm
INSTALL_DIR ?= installation_prefix
# check if already exists.

LIBRARY := utilities.h
# if in the same folder, then no need to write it.
SOURCES := main.cpp utilites_floats.cpp utilites_ints.cpp
OBJECTS := $(SOURCES:.cpp=.o)

# $@ is the name of file being created by the rule.
# $^ is the list of dependencies.

app: $(OBJECTS)
	$(QUIET)$(ECHO) "building app!"
	$(QUIET)$(CC) -o $@ $^
	$(QUIET)$(RM) -f *.o 
# remove *.o after building

# https://www.gnu.org/software/make/manual/html_node/Automatic-Variables.html
%.o: %.cpp $(LIBRARY)
	$(QUIET)$(ECHO) "compiling $< ..."
	$(CC) $(CXXFLAGS) -o "$@" -c $<
# < means source file
	

install_dir:
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then mkdir "$(INSTALL_DIR)" ; fi
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then echo "$(INSTALL_DIR) is not created" ; exit 1 ; fi
# after if, use fi to end

install: install_dir
	install -m 755 app "$(INSTALL_DIR)/math_app"

default: app

.PHONY: clean distclean install_dir

distclean: clean
	$(QUIET)$(ECHO) "removing app....!"
	$(QUIET)$(RM) -f app

clean:
	$(QUIET)$(ECHO) "removing all object files!"
	$(QUIET)$(RM) -f *.o

