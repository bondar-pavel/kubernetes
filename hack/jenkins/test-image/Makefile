# Copyright 2016 The Kubernetes Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

all: push

# Tag format: $GO_VERSION-$EMBEDDED_DOCKER_VERSION-$REVISION
# These versions are specified in the Dockerfile
TAG = go1.6.3-docker1.9.1-rev2

container:
	docker build -t gcr.io/google_containers/kubekins-test .
	docker tag gcr.io/google_containers/kubekins-test gcr.io/google_containers/kubekins-test:$(TAG)

push: container
	gcloud docker push gcr.io/google_containers/kubekins-test # Push image tagged as latest to repository
	gcloud docker push gcr.io/google_containers/kubekins-test:$(TAG) # Push version tagged image to repository (since this image is already pushed it will simply create or update version tag)

clean:
