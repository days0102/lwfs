# not a GNU package. You can remove this line, if
# have all needed files, that a GNU package needs
AUTOMAKE_OPTIONS = foreign 1.4

SUBDIRS = 

SUBDIRS += src 


if BUILD_DOCS
SUBDIRS += doc
endif


test:
	echo LWFS_ROOT = $(LWFS_ROOT)
	echo DIRS = $(DIRS)
	echo SUBDIRS = $(SUBDIRS)

cp:
	@mkdir -p fuse/.libs
	@mkdir -p fuse/.bins
	@echo "Checking library files..."
	@if [ ! -f "src/client/.libs/liblwfs_client.so.0.0.0" ]; then \
		echo "Error: liblwfs_client.so.0.0.0 not found"; \
		exit 1; \
	fi
	@cp -v src/client/.libs/liblwfs_client.so.0.0.0 fuse/.libs/
	@cd fuse/.libs && \
		ln -sf liblwfs_client.so.0.0.0 liblwfs_client.so && \
		ln -sf liblwfs_client.so.0.0.0 liblwfs_client.so.0

	@if [ ! -f "src/client/.libs/liblwfs_client.a" ]; then \
		echo "Error: liblwfs_client.a not found"; \
		exit 1; \
	fi
	@cp -v src/client/.libs/liblwfs_client.a fuse/.libs/

	@if [ ! -f "src/server/.libs/liblwfs_server.so.0.0.0" ]; then \
		echo "Error: liblwfs_server.so.0.0.0 not found"; \
		exit 1; \
	fi
	@cp -v src/server/.libs/liblwfs_server.so.0.0.0 fuse/.libs/
	@cd fuse/.libs && \
		ln -sf liblwfs_server.so.0.0.0 liblwfs_server.so && \
		ln -sf liblwfs_server.so.0.0.0 liblwfs_server.so.0

	@if [ ! -f "src/server/.libs/liblwfs_server.a" ]; then \
		echo "Error: liblwfs_server.a not found"; \
		exit 1; \
	fi
	@cp -v src/server/.libs/liblwfs_server.a fuse/.libs/

	@if [ ! -f "src/common/.libs/libcommon.a" ]; then \
		echo "Error: libcommon.a not found"; \
		exit 1; \
	fi
	@cp -v src/common/.libs/libcommon.a fuse/.libs/

	@if [ ! -f "src/server/naming_server/lwfs-naming-server" ]; then \
		echo "Error: lwfs-naming-server not found"; \
		exit 1; \
	fi
	@cp -v src/server/naming_server/lwfs-naming-server fuse/.bins/

	@if [ ! -f "src/server/authr_server/lwfs-authr" ]; then \
		echo "Error: lwfs-authr not found"; \
		exit 1; \
	fi
	@cp -v src/server/authr_server/lwfs-authr fuse/.bins/

	@if [ ! -f "src/server/storage_server/lwfs-ss" ]; then \
		echo "Error: lwfs-ss not found"; \
		exit 1; \
	fi
	@cp -v src/server/storage_server/lwfs-ss fuse/.bins/


CLEANFILES = *~
