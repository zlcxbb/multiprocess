SOURCEDIR := .
INCLUDEDIR := .
BUILD_DIR := .
CURRENTDIR := .
EXE := $(BUILD_DIR)/client
CC := g++
LIBS := pthread
SOURCES := $(wildcard $(SOURCEDIR)/*.cpp $(SOURCEDIR)/*.c)
OBJS := $(patsubst %.c, %.o, $(patsubst %.cpp, %.o, $(SOURCES))) 
RM := rm -rf
CXXFLAGS := -Wall -g -O -std=c++0x -DDEBUG -DTCP_SOCKET -DDELAY

start: prepare $(EXE)

prepare: 
	mkdir -p $(BUILD_DIR)

$(EXE): $(OBJS)
	$(CC) -o $@ $(OBJS) $(addprefix -l, $(LIBS));

#$(CURRENTDIR)/%.o: $(CURRENTDIR)/%.cpp
#	$(CC) $(addprefix -I, $(INCLUDEDIR)) $(addprefix -I, $(SOURCEDIR)) $(addprefix -I, $(CURRENTDIR)) -c $(CXXFLAGS) %< -o %@

$(SOURCEDIR)/%.o: $(SOURCEDIR)/%.cpp $(INCLUDEDIR)/%.h
	$(CC) -c $(CXXFLAGS) %< -o %@

.PHONY: clean rebuild
clean:
	$(RM) $(EXE)
	$(RM) $(SOURCEDIR)/*.o
	$(RM) $(CURRENTDIR)/*.o
	$(RM) $(SOURCEDIR)/log/*.log
rebuild: clean start


