/opt/perl/bin/cpan # install

test creates a nyt prof directory

in filterd, use ./benchmark.pl
-t = #of items, -t 1 = 1 item
-T = time, -T 10 = 10 seconds
-i = userid
./benchmark.pl -t 1 -i 180
craetes nytprof.out

in eventd, we can add '-d:NYTProf' to evend.pl

run "nytprofhtml"
this creates a directory with the html results

