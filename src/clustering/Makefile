include ../../config

EXECS= test_data_clustering

OBJS= arc_netcdf_file.o netcdf_file.o file.o clust.o main.o

EXTERN_OBJS= ./core/data_netcdf.o

EXTERN_SRC= ./core/data_netcdf.cpp

NETCDF_LIBS= -lnetcdf -lnetcdf_c++

SOURCE= arc_netcdf_file.cpp netcdf_file.cpp file.cpp clust.cpp main.cpp
	
all: $(EXECS)
	
$(EXTERN_OBJS): 
	$(MAKE) -C ./core


%.o: %.cpp
	$(CXX) $(CXX_FLAGS) $(CXX_INCLUDE) $(NETCDF_INCLUDE) -c -o $@  $^
 	
$(EXECS): $(OBJS) $(EXTERN_OBJS)
	$(CXXLINKER) $(CXXLINKER_FLAGS) -o $@ $^ $(NETCDF_LIBS) -lrfftw -lfftw -lm
	
install: $(EXECS)
	cp -rf $^ $(INSTALL_DIR)/bin
	
clean:
	$(MAKE) -C ./core clean
	rm -f $(EXECS) *.o

.PHONY: clean
