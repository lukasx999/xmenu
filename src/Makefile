include config.mk

CFLAGS=-Wall -Wextra -ggdb -std=c99 -pedantic -O3 `pkg-config --cflags x11 xft`
LIBS=-lm `pkg-config --libs x11 xft`
DEPS=ui.h sort.h config.h
FILES=main.o ui.o sort.o
BIN=xmenu

all: xmenu

xmenu: $(FILES) $(DEPS)
	@$(CC) $(CFLAGS) $(LIBS) $^ -o $(BIN)
	@echo CC $^

%.o: %.c Makefile $(DEPS)
	@$(CC) $(CFLAGS) -c $< -o $@
	@echo CC $<

clean:
	rm *.o $(BIN)

install: all
	cp -f xmenu $(INSTALL_DIR)
	cp -f xmenu_run.sh $(INSTALL_DIR)/xmenu_run

uninstall:
	rm -f $(INSTALL_DIR)/xmenu $(INSTALL_DIR)/xmenu_run

.PHONY: clean install uninstall
