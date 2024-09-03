

# 定义编译器和工具
CXX := g++
VERILATOR := verilator

# 定义编译选项
CXXFLAGS := -Wall -I$(SYSTEMC_INCLUDE)
LDFLAGS := -L$(SYSTEMC_LIBDIR) -lsc -lpthread

# 定义目标文件
TARGET := obj_dir/Vour

# 默认目标
all: $(TARGET)


# 使用 Verilator 生成 SystemC 模型
Vour.mk: sc_main.cpp our.v
	$(VERILATOR) --sc --exe -Wall sc_main.cpp our.v

# 编译生成的目标
$(TARGET): Vour.mk
	make -j -C obj_dir -f Vour.mk Vour

# 运行模拟
run: $(TARGET)
	./$(TARGET)

# 清理生成的文件
clean:
	rm -rf obj_dir test_our_sc

.PHONY: all test_our_sc our.v sc_main.cpp Vour.mk $(TARGET) run clean