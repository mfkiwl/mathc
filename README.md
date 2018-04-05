# MATHC

[![Build Status](https://travis-ci.org/ferreiradaselva/mathc.svg?branch=master)](https://travis-ci.org/ferreiradaselva/mathc)

MATHC is a simple math library for 2D and 3D programming. It contains implementations for:

- Vectors (2D, 3D and 4D)
- Quaternions
- Matrices (2×2, 3×3, and 4×4)
- Easing functions

## Configuring

MATHC can be configured using preprocessors:

- `mint_t`: the integer type, which is `int32_t` by default. Can be used to define `mint_t` as any other integer type.
- `mfloat_t`: the floating-point, which is `float` by default. Can be used to define `mfloat_t` as any other floating-point type.
- `MATHC_USE_INT64`: define `mint_t` as `int64_t`.
- `MATHC_USE_DOUBLE`: define `mfloat_t` as `double`.
- `MATHC_DOUBLE_PRECISION`: use the standard math functions with double precision.
- `MATHC_NO_POINTER_STRUCT_FUNCTIONS`: don't define functions that take pointer to structures.
- `MATHC_NO_STRUCT_FUNCTIONS`: don't define functions that take structures as value.
- `MATHC_NO_EASING_FUNCTIONS`: don't define easing functions.

## Types

By default, types are can be declared as `mfloat_t` arrays, `mint_t` arrays, or structures:

```c
/* As float arrays */
mfloat_t texture_coordinates[VEC2_SIZE];
mfloat_t position[VEC3_SIZE];
mfloat_t rgba[VEC4_SIZE];
mfloat_t rotation[QUAT_SIZE];
mfloat_t rotation_mat[MAT3_SIZE];
mfloat_t model_mat[MAT4_SIZE];

/* As float structures */
struct vec2 texture_coordinates;
struct vec3 position;
struct vec4 rgba;
struct quat rotation;
struct mat3 rotation_mat;
struct mat4 model_mat;

/* As integer arrays */
mint_t texture_coordinates[VEC2_SIZE];
mint_t position[VEC3_SIZE];
mint_t rgba[VEC4_SIZE];

/* As integer structures */
struct vec2i texture_coordinates;
struct vec3i position;
struct vec4i rgba;
```

## Functions

By default, MATHC has functions that take as argument `mfloat_t` arrays, `mint_t` arrays, structures as value, or pointers to structure:

```c
/* As array */
mfloat_t position[VEC3_SIZE];
mfloat_t offset[VEC3_SIZE];

vec2_add(position,
	vec2(position, 0.0f, 0.0f),
	vec2(offset, 1.0f, 1.0f));

/* As structure value */
struct vec2 position = svec2(0.0f, 0.0f);
struct vec2 offset = svec2(1.0f, 1.0f);
position = svec2_add(position, offset);

/* As structure pointer */
struct vec2 position;
struct vec2 offset;
psvec2(&position, 0.0f, 0.0f)
psvec2(&offset, 1.0f, 1.0f)
psvec2_add(&position, &position, &offset);
```

Functions that take structure as value have a prefix `s`. Functions that take structure pointers have a prefix `ps`.

## Easing Functions

The easing functions are an implementation of the functions presented in [easings.net](http://easings.net/), useful particularly for animations.

Easing functions take a value inside the range `0.0-1.0` and usually will return a value inside that same range. However, in some of the easing functions, the returned value extrapolate that range (Check the [easings.net](http://easings.net/) to see those functions).

# License

Copyright © 2018 Felipe Ferreira da Silva

This software is provided 'as-is', without any express or implied warranty. In no event will the authors be held liable for any damages arising from the use of this software.

Permission is granted to anyone to use this software for any purpose, including commercial applications, and to alter it and redistribute it freely, subject to the following restrictions:

1. The origin of this software must not be misrepresented; you must not claim that you wrote the original software. If you use this software in a product, an acknowledgment in the product documentation would be appreciated but is not required.
2. Altered source versions must be plainly marked as such, and must not be misrepresented as being the original software.
3. This notice may not be removed or altered from any source distribution.
