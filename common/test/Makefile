COMMON_TEST_SRC := $(wildcard common/test/run-*.c)
COMMON_TEST_OBJS := $(COMMON_TEST_SRC:.c=.o)
COMMON_TEST_PROGRAMS := $(COMMON_TEST_OBJS:.o=)

COMMON_TEST_COMMON_OBJS :=				\
	common/utils.o

$(COMMON_TEST_PROGRAMS): $(COMMON_TEST_COMMON_OBJS) $(BITCOIN_OBJS)
$(COMMON_TEST_OBJS): $(COMMON_HEADERS) $(WIRE_HEADERS) $(COMMON_SRC)

ALL_TEST_PROGRAMS += $(COMMON_TEST_PROGRAMS)
ALL_OBJS += $(COMMON_TEST_PROGRAMS:=.o)

# Sphinx test wants to decode TLVs.
common/test/run-sphinx: wire/gen_onion_wire.o wire/towire.o wire/fromwire.o

update-mocks: $(COMMON_TEST_SRC:%=update-mocks/%)

check-units: $(COMMON_TEST_PROGRAMS:%=unittest/%)
