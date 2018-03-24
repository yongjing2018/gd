CC = gcc
CXX = g++
CFLAGS = -O -DDBG -D_REENTRANT -Wall -DUSE_PTHREAD -pthread
LDFLAGS = -ldl -lm

#wildcard 对 c文件进行展开
SRCS = $(wildcard *.c) $(wildcard *.cpp) 
#去除路径信息
dir=$(notdir $(SRCS))
# 把后缀.c 替换成 .o
OBJS = $(patsubst %.c, %.o, $(patsubst %.cpp, %.o,$(dir))  )

#OBJS = main1.o main.o

#DATALIBS = dblib/lib.a
#ZIPLIBS = ZipCoder/ZipCoder.a  

TARGET = tcp_server tcp_client
all: $(TARGET)
	@echo $(SRCS)
	@echo $(dir)
	@echo $(OBJS)
tcp_server : tcp_server.o $(filter-out tcp_client.o tcp_server.o,$(OBJS)) 
	$(CXX) $(CFLAGS) -o $@ $^ $(LDFLAGS)
tcp_client : tcp_client.o $(filter-out tcp_client.o tcp_server.o,$(OBJS))
	$(CXX) $(CFLAGS) -o $@ $^ $(LDFLAGS)



%.o : %.c
	$(CC) -c $(CFLAGS)  $^ -o $@
%.o : %.cpp
	$(CXX) -c $(CFLAGS) $^ -o $@    

.PHONY : clean
clean :
	rm -f *.o
	rm -f ../bin/excute
	rm -f $(TARGET)

# install:
#         mv Excute excute; cp -f ordermisd ../bin/;
