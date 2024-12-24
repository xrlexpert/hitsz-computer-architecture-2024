#FOR run_simd.c
# 设置编译器
CC = gcc

# 编译选项
CFLAGS = -O3 -mavx2 -fopenmp -march=native

# 默认目标，编译 run.c 和 runq.c
.PHONY: run
run: run.c
	$(CC) $(CFLAGS) -o run run.c -lm

# 如果需要调试版本
.PHONY: rundebug
rundebug: run.c
	$(CC) -g -O0 -fopenmp -o run run.c -lm

# 优化版本，开启更多优化选项
.PHONY: runfast
runfast: run.c
	$(CC) -Ofast -mavx2 -fopenmp -march=native -o run run.c -lm

# 用于 Windows 的版本
.PHONY: win64
win64:
	x86_64-w64-mingw32-gcc -Ofast -D_WIN32 -o run.exe -I. run.c win.c
	x86_64-w64-mingw32-gcc -Ofast -D_WIN32 -o runq.exe -I. runq.c win.c

# 用于GNU标准
.PHONY: rungnu
rungnu:
	$(CC) -Ofast -std=gnu11 -mavx2 -fopenmp -march=native -o run run.c -lm

# 清理中间文件
.PHONY: clean
clean:
	rm -f run
	rm -f runq
