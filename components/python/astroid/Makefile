#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# This file was automatically generated using the following command:
#   $WS_TOOLS/python-integrate-project astroid
#

BUILD_STYLE = pyproject

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME =		astroid
HUMAN_VERSION =			3.3.8
COMPONENT_SUMMARY =		An abstract syntax tree for Python with inference support.
COMPONENT_ARCHIVE_HASH =	\
	sha256:a88c7994f914a4ea8572fac479459f4955eeccc877be3f2d959a33273b0cf40b
COMPONENT_LICENSE =		LGPL-2.1-only
COMPONENT_LICENSE_FILE =	LICENSE

include $(WS_MAKE_RULES)/common.mk

# https://github.com/pylint-dev/astroid/issues/2392
PYTEST_ADDOPTS += --deselect tests/brain/test_dataclasses.py::test_pydantic_field
# fails with tox-current-env
PYTEST_ADDOPTS += --deselect tests/test_modutils.py::GetModulePartTest::test_known_values_get_builtin_module_part
# https://github.com/pylint-dev/astroid/issues/2442
PYTEST_ADDOPTS += --deselect tests/brain/numpy/test_core_einsumfunc.py::test_numpy_function_calls_inferred_as_ndarray
PYTEST_ADDOPTS += --deselect tests/brain/numpy/test_core_fromnumeric.py::BrainNumpyCoreFromNumericTest::test_numpy_function_calls_inferred_as_ndarray
PYTEST_ADDOPTS += --deselect tests/brain/numpy/test_core_multiarray.py::BrainNumpyCoreMultiarrayTest::test_numpy_function_calls_inferred_as_ndarray
PYTEST_ADDOPTS += --deselect tests/brain/numpy/test_core_numerictypes.py::NumpyBrainCoreNumericTypesTest::test_datetime_astype_return
PYTEST_ADDOPTS += --deselect tests/brain/numpy/test_core_numerictypes.py::NumpyBrainCoreNumericTypesTest::test_generic_types_are_subscriptables
PYTEST_ADDOPTS += --deselect tests/brain/numpy/test_core_umath.py::NumpyBrainCoreUmathTest::test_numpy_core_umath_functions_return_type
PYTEST_ADDOPTS += --deselect tests/test_regrtest.py::NonRegressionTests::test_numpy_distutils

# Random temporary dir name
COMPONENT_TEST_TRANSFORMS += "-e 's|\(/tmp\).\{8\}/|\1XXXXXXXX/|g'"
# Random temporary file name
COMPONENT_TEST_TRANSFORMS += "-e 's|\(/tmp\).\{8\}\.py|\1XXXXXXXX.py|g'"

# Auto-generated dependencies
PYTHON_REQUIRED_PACKAGES += library/python/setuptools
PYTHON_REQUIRED_PACKAGES += library/python/typing-extensions
PYTHON_REQUIRED_PACKAGES += library/python/wheel
PYTHON_REQUIRED_PACKAGES += runtime/python
TEST_REQUIRED_PACKAGES.python += library/python/attrs
TEST_REQUIRED_PACKAGES.python += library/python/black
TEST_REQUIRED_PACKAGES.python += library/python/coverage
TEST_REQUIRED_PACKAGES.python += library/python/mypy
TEST_REQUIRED_PACKAGES.python += library/python/nose
TEST_REQUIRED_PACKAGES.python += library/python/numpy
TEST_REQUIRED_PACKAGES.python += library/python/pylint
TEST_REQUIRED_PACKAGES.python += library/python/pytest
TEST_REQUIRED_PACKAGES.python += library/python/pytest-cov
TEST_REQUIRED_PACKAGES.python += library/python/python-dateutil
TEST_REQUIRED_PACKAGES.python += library/python/regex
TEST_REQUIRED_PACKAGES.python += library/python/setuptools
TEST_REQUIRED_PACKAGES.python += library/python/six
TEST_REQUIRED_PACKAGES.python += library/python/typing-extensions
TEST_REQUIRED_PACKAGES.python += library/python/urllib3
