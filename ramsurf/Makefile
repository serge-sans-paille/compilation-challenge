FC=gfortran

TARGET=ramsurf1.5
TIMELOG=.timings

all:$(TARGET)

check:$(TARGET)
	./$(TARGET)
	cmp tl.grid ref.grid
	cmp tl.line ref.line

clean:
	$(RM) $(TARGET)

bench:all
	@$(RM) $(TIMELOG)
	@for i in `seq 10` ; do /usr/bin/time -a -p -f '%e' -o $(TIMELOG) ./$(TARGET) ; done
	@python -c 'import sys ; l = map(float,sys.stdin) ; print sum(l)/len(l)' < $(TIMELOG)

