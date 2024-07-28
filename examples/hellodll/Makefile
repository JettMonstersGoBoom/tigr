CFLAGS += -I../.. -Os -s -DTIGR_SHARED
ifeq ($(OS),Windows_NT)
	LDFLAGS += -s -lopengl32 -lgdi32
	DLL = dll
	EXT = exe
else
	UNAME_S := $(shell uname -s)
	DLL = so
	EXT = 
	ifeq ($(UNAME_S),Darwin)
		LDFLAGS += -framework OpenGL -framework Cocoa
	else ifeq ($(UNAME_S),Linux)
		LDFLAGS += -s -lGLU -lGL -lX11
	endif
endif


hello.$(EXT) : hello.c tigr.$(DLL) 
	gcc $^ -Os -o $@ $(CFLAGS) $(LDFLAGS)

tigr.$(DLL):
	gcc ../../tigr.c -DTIGR_BUILDSHARED -shared $(CFLAGS) $(LDFLAGS) -o tigr.$(DLL)

clean:
	rm hello.$(ext)
