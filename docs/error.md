```shell


====================[ Build | testodbrelationship | Debug ]=====================
/root/clion-2018.2.6/bin/cmake/linux/bin/cmake --build /root/CLionProjects/testodbrelationship/cmake-build-debug --target testodbrelationship -- -j 1
[ 33%] Building CXX object CMakeFiles/testodbrelationship.dir/driver.cxx.o
In file included from /root/CLionProjects/testodbrelationship/driver.cxx:11:0:
/root/CLionProjects/testodbrelationship/database.hxx:35:13: warning: ‘template<class> class std::auto_ptr’ is deprecated [-Wdeprecated-declarations]
 inline std::auto_ptr<odb::database>
             ^
In file included from /opt/rh/devtoolset-4/root/usr/include/c++/5.2.1/memory:81:0,
                 from /root/CLionProjects/testodbrelationship/driver.cxx:4:
/opt/rh/devtoolset-4/root/usr/include/c++/5.2.1/bits/unique_ptr.h:49:28: note: declared here
   template<typename> class auto_ptr;
                            ^
In file included from /root/CLionProjects/testodbrelationship/driver.cxx:11:0:
/root/CLionProjects/testodbrelationship/database.hxx: In function ‘std::auto_ptr<odb::database> create_database(int&, char**)’:
/root/CLionProjects/testodbrelationship/database.hxx:62:3: warning: ‘template<class> class std::auto_ptr’ is deprecated [-Wdeprecated-declarations]
   auto_ptr<database> db (new odb::mysql::database (argc, argv));
   ^
In file included from /opt/rh/devtoolset-4/root/usr/include/c++/5.2.1/memory:81:0,
                 from /root/CLionProjects/testodbrelationship/driver.cxx:4:
/opt/rh/devtoolset-4/root/usr/include/c++/5.2.1/bits/unique_ptr.h:49:28: note: declared here
   template<typename> class auto_ptr;
                            ^
/root/CLionProjects/testodbrelationship/driver.cxx: In function ‘int main(int, char**)’:
/root/CLionProjects/testodbrelationship/driver.cxx:43:5: warning: ‘template<class> class std::auto_ptr’ is deprecated [-Wdeprecated-declarations]
     auto_ptr<database> db (create_database (argc, argv));
     ^
In file included from /opt/rh/devtoolset-4/root/usr/include/c++/5.2.1/memory:81:0,
                 from /root/CLionProjects/testodbrelationship/driver.cxx:4:
/opt/rh/devtoolset-4/root/usr/include/c++/5.2.1/bits/unique_ptr.h:49:28: note: declared here
   template<typename> class auto_ptr;
                            ^
In file included from /usr/local/include/odb/database.hxx:631:0,
                 from /root/CLionProjects/testodbrelationship/driver.cxx:7:
/usr/local/include/odb/database.ixx: In instantiation of ‘typename odb::object_traits<T>::id_type odb::database::persist(const P<T>&) [with T = employer; P = std::tr1::shared_ptr; typename odb::object_traits<T>::id_type = std::basic_string<char>]’:
/usr/local/include/odb/database.ixx:220:26:   required from ‘typename odb::object_traits<T>::id_type odb::database::persist(P<T>&) [with T = employer; P = std::tr1::shared_ptr; typename odb::object_traits<T>::id_type = std::basic_string<char>]’
/root/CLionProjects/testodbrelationship/driver.cxx:65:24:   required from here
/usr/local/include/odb/database.ixx:195:34: error: invalid initialization of reference of type ‘employer* const&’ from expression of type ‘const std::tr1::shared_ptr<employer>’
     const object_pointer& pobj (p);
                                  ^
/usr/local/include/odb/database.ixx: In instantiation of ‘typename odb::object_traits<T>::id_type odb::database::persist(const P<T>&) [with T = project; P = std::tr1::shared_ptr; typename odb::object_traits<T>::id_type = std::basic_string<char>]’:
/usr/local/include/odb/database.ixx:220:26:   required from ‘typename odb::object_traits<T>::id_type odb::database::persist(P<T>&) [with T = project; P = std::tr1::shared_ptr; typename odb::object_traits<T>::id_type = std::basic_string<char>]’
/root/CLionProjects/testodbrelationship/driver.cxx:67:24:   required from here
/usr/local/include/odb/database.ixx:195:34: error: invalid initialization of reference of type ‘project* const&’ from expression of type ‘const std::tr1::shared_ptr<project>’
/usr/local/include/odb/database.ixx: In instantiation of ‘typename odb::object_traits<T>::id_type odb::database::persist(const P<T>&) [with T = employee; P = std::tr1::shared_ptr; typename odb::object_traits<T>::id_type = long unsigned int]’:
/usr/local/include/odb/database.ixx:220:26:   required from ‘typename odb::object_traits<T>::id_type odb::database::persist(P<T>&) [with T = employee; P = std::tr1::shared_ptr; typename odb::object_traits<T>::id_type = long unsigned int]’
/root/CLionProjects/testodbrelationship/driver.cxx:70:26:   required from here
/usr/local/include/odb/database.ixx:195:34: error: invalid initialization of reference of type ‘employee* const&’ from expression of type ‘const std::tr1::shared_ptr<employee>’
/usr/local/include/odb/database.ixx: In instantiation of ‘void odb::database::update(const P<T>&) [with T = employee; P = std::tr1::shared_ptr]’:
/usr/local/include/odb/database.ixx:388:18:   required from ‘void odb::database::update(P<T>&) [with T = employee; P = std::tr1::shared_ptr]’
/root/CLionProjects/testodbrelationship/driver.cxx:143:23:   required from here
/usr/local/include/odb/database.ixx:363:34: error: invalid initialization of reference of type ‘employee* const&’ from expression of type ‘const std::tr1::shared_ptr<employee>’
     const object_pointer& pobj (p);
                                  ^
gmake[3]: *** [CMakeFiles/testodbrelationship.dir/driver.cxx.o] 错误 1
gmake[2]: *** [CMakeFiles/testodbrelationship.dir/all] 错误 2
gmake[1]: *** [CMakeFiles/testodbrelationship.dir/rule] 错误 2
gmake: *** [testodbrelationship] 错误 2

```

do this to resolve it

```shell

odb -d mysql --generate-schema --generate-query --generate-session --default-pointer std::tr1::shared_ptr employee.hxx

```
