# botantest
Worlds smallest program that isn't hello world.

Set the BOTANINST env var to the install directory for botan 1.11 and then try to compile this program with MSVS 2013
The following commands should do it when issued from an VS2013 x86 command prompt:

```
set BOTANINST=%USERPROFILE%\install
configure.py --disable-shared --disable-modules=selftest,tls --prefix=%BOTANINST% --build-mode=debug --cpu=i386 --via-amalgamation --maintainer-mode
nmake install
devenv
```
Then open the botantest.sln project with MSVS, and compile (Note: the project also uses the env var BOTANINST). It should produce the following link error:
```
botan-1.11.lib(botan_all.obj) : error LNK2005: "public: unsigned int __thiscall Botan::BigInt::bytes(void)const " (?bytes@BigInt@Botan@@QBEIXZ) already defined in botantest.obj
```