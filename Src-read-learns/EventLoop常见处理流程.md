### EventLoop与IO复用技术

one thread one loop
一般是一个loop管理多个fd


while (!m_bQuit) {
    check_and_do_timers();   // 检测定时器（执行过期回调函数）
    
    epoll_or_select_func();   // IO多路复用检测（连接、读、写）
 
    handle_io_events();     // 一般是执行IO多路复用绑定fd的回调函数：从缓存区数据、文件io()
 
    handle_other_things();  // other
}

