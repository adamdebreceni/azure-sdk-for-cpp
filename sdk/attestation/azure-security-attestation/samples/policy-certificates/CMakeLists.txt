# Copyright (c) Microsoft Corporation.
# Licensed under the MIT License.

cmake_minimum_required (VERSION 3.13)

project (attestation-policy LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED True)

macro (define_sample samplename)
add_executable (
  attestation-${samplename}
  ${samplename}.cpp)

CREATE_PER_SERVICE_TARGET_BUILD_FOR_SAMPLE(attestation-${samplename} attestation)

target_link_libraries(attestation-${samplename} PRIVATE azure-security-attestation azure-identity OpenSSL::Crypto get-env-helper)

endmacro()

DEFINE_SAMPLE(get_policy_certificates)
DEFINE_SAMPLE(add_policy_certificate)
