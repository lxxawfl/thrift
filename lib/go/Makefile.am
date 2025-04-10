#
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements. See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership. The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License. You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied. See the License for the
# specific language governing permissions and limitations
# under the License.
#

SUBDIRS = .

if WITH_TESTS
SUBDIRS += test test/fuzz
endif

if GOVERSION_GE_118
GOBUILDEXTRA = -buildvcs=false
else
GOBUILDEXTRA =
endif

install:
	@echo '##############################################################'
	@echo '##############################################################'
	@echo 'The Go client library should be installed via "go get", please see /lib/go/README.md'
	@echo '##############################################################'
	@echo '##############################################################'

# NOTE: We have to disable stdmethods in go vet until
# https://github.com/golang/go/issues/52445 is fixed.
check-local:
	$(GO) vet -mod=mod -stdmethods=false github.com/apache/thrift/lib/go/thrift
	$(GO) test -mod=mod -race ./thrift

clean-local:
	$(RM) -rf pkg

all-local:
	$(GO) build $(GOBUILDEXTRA) -mod=mod ./thrift

EXTRA_DIST = \
	thrift \
	coding_standards.md \
	README.md
