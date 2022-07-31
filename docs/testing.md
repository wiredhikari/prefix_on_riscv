`emerge -q1 --onlydeps  --with-test-deps=y ${cat}/${pkg}`
Add keywords in file `package.accept_keywords`, then emerge test dependencies, finally `USE=test emerge */*`
