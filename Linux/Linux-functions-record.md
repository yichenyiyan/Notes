# ZN (阅读源代码时遇到的未使用过的函数)

char *strchr(const char *s, int c);
strchr() 函数返回指向字符串 s 中字符 c 第一次出现的指针。

int atoi(const char *nptr);
atoi() 函数将 nptr 指向的字符串的初始部分转换为 int。其行为与
strtol(nptr, NULL, 10); 相同，但 atoi() 不会检测错误。
atol() 和 atoll() 函数的行为与 atoi() 相同，但它们会将字符串的初始部分转换为其返回类型 long 或 long long。