# Ada-Shared-Library
An example of a shared library in Ada, stolen from Adacore Gems articles:

http://www.adacore.com/adaanswers/gems/gem-109-ada-plug-ins-and-shared-libraries-part-1/

http://www.adacore.com/adaanswers/gems/gem-110-ada-plug-ins-and-shared-libraries-part-2/

"Note that the use of shared libraries reduces the size of the final executable and can also reduce the memory footprint at execution time when the library is shared among several executables."

https://stackoverflow.com/questions/26805533/how-to-create-an-ada-lib-a-and-link-to-c-updated

https://stackoverflow.com/questions/25117653/gnat-gprbuild-how-to-build-a-dynamic-dll-and-link-with-a-static-c-library

The sample project builds on my machine with output:

    gprbuild -d -P/home/iosif/Documents/dev/Ada/Ada_Shared_Library/default.gpr -p
    object directory "/home/iosif/Documents/dev/Ada/Ada_Shared_Library/obj/" created
    library directory "/home/iosif/Documents/dev/Ada/Ada_Shared_Library/lib" created for project default
    library ALI directory "/home/iosif/Documents/dev/Ada/Ada_Shared_Library/libali" created for project default
    library source copy directory "/home/iosif/Documents/dev/Ada/Ada_Shared_Library/libsrc/" created for project  default
    gnatgcc -c -fPIC lib1.adb
    gprlib logging.lexch
    gnatbind -n -o b__logging.adb -Llogging /home/iosif/Documents/dev/Ada/Ada_Shared_Library/obj/lib1.ali
    gnatgcc -c -x ada -gnatA -gnatws b__logging.adb -o b__logging.o ...
    gnatgcc -shared -o /home/iosif/Documents/dev/Ada/Ada_Shared_Library/lib/1.0.0 ... 
    /home/iosif/Documents/dev/Ada/Ada_Shared_Library/obj/lib1.o ...
    [2016-05-25 09:01:20] process terminated successfully, elapsed time: 01.41s
    
with `/home/iosif/Documents/dev/Ada/Ada_Shared_Library/lib/liblogging.so` linking to `1.0.0`.
