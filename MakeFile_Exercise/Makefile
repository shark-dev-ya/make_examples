#Some defitions here:
CC := g++
CXXFLAGS := -std=c++17
QUIET := @
ECHO := echo
RM := rm
INSTALL_DIR ?= installation_prefix

SOURCES := main.cpp utilites_floats.cpp utilites_ints.cpp
OBJECTS := $(SOURCES:.cpp=.o)

# $@ is the name of file being created by the rule.
# $^ is the list of dependencies.

get_your_shit_together: $(OBJECTS)
	$(QUIET)$(ECHO) "building app!"
	$(QUIET)$(CC) -o $@ $^

# https://www.gnu.org/software/make/manual/html_node/Automatic-Variables.html
%.o: %.cpp 
	$(QUIET)$(ECHO) "compiling $< ..."
	@$(CC) $(CXXFLAGS) -o "$@" -c $<

install_dir:
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then mkdir "$(INSTALL_DIR)" ; fi
	$(QUIET)if [ ! -d "$(INSTALL_DIR)" ]; then echo "$(INSTALL_DIR) is not created" ; exit 1 ; fi

install: install_dir
	install -m 755 get_your_shit_together "$(INSTALL_DIR)/get_your_shit_together"

default: get_your_shit_together

.PHONY: clean distclean install_dir

distclean: clean
	$(QUIET)$(ECHO) "removing app....!"
	$(QUIET)$(RM) -f get_your_shit_together

clean:
	$(QUIET)$(ECHO) "removing all object files!"
	$(QUIET)$(RM) -f *.o