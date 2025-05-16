CC = gcc
CFLAGS = -Wall -D_FILE_OFFSET_BITS=64 -DFUSE_USE_VERSION=22 -g
INCLUDES = -I. -I.. -I../src -I../src/common -I../src/client -I../src/support
LDFLAGS = -lfuse -lpthread -I/usr/lib -ltirpc -L../src/support/.libs -lsupport \
-L../src/server/.libs -llwfs_server \
-L../src/client/.libs -llwfs_client \
-L../src/common/.libs -lcommon \
-L/usr/local/BerkeleyDB.4.2/lib -ldb \

# 目标文件
TARGETS = fuse-lwfs

# export LD_LIBRARY_PATH=${PWD}/.libs:/usr/local/BerkeleyDB.4.2/lib:${LD_LIBRARY_PATH}

# 默认目标
all: $(TARGETS)

# 编译 fuse-lwfs
fuse-lwfs: fuse-lwfs.c fuse-callbacks.c fuse-debug.c
	$(CC) $(CFLAGS) $(INCLUDES) -o $@ $^ $(LDFLAGS)

# 编译 lwfsfuse
lwfsfuse: lwfsfuse.c
	$(CC) $(CFLAGS) $(INCLUDES) -o $@ $< $(LDFLAGS)

# 清理
clean:
	rm -f $(TARGETS) *.o

.PHONY: all clean

ns:
	LD_LIBRARY_PATH=${PWD}/.libs:/usr/local/BerkeleyDB.4.2/lib:$$LD_LIBRARY_PATH PTL_IFACE=lo ../src/server/naming_server/lwfs-naming-server

as:
	LD_LIBRARY_PATH=${PWD}/.libs:/usr/local/BerkeleyDB.4.2/lib:$$LD_LIBRARY_PATH PTL_IFACE=lo ../src/server/authr_server/lwfs-authr

ss:
	LD_LIBRARY_PATH=${PWD}/.libs:/usr/local/BerkeleyDB.4.2/lib:$$LD_LIBRARY_PATH PTL_IFACE=lo ../src/server/storage_server/lwfs-ss

env:
	. ./fuse-lwfs.env
# export LD_LIBRARY_PATH=/home/lwz/lwfs/src/common/.libs:/home/lwz/lwfs/src/client/.libs:/home/lwz/lwfs/src/server/.libs:/usr/local/BerkeleyDB.4.2/lib:/home/lwz/lwfs/src/client/.libs:${LD_LIBRARY_PATH}