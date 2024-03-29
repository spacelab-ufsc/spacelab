# Contribution Guidelines

## Preamble

All authored content must contain appropriate preamble including copyright and licence information as shown here:

```
/*
 * file.c
 * 
 * Copyright (C) 2021, SpaceLab.
 * 
 * This file is part of PROJECT_NAME.
 * 
 * PROJECT_NAME is free software: you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 * 
 * PROJECT_NAME is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
 * GNU General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with PROJECT_NAME. If not, see <http://www.gnu.org/licenses/>.
 * 
 */
```

All source code files must also contain a brief description, list of authors (with e-mails, one per line), date of creation and the doxygen group (when applicable), as presented below:

```
/**
 * \brief Brief description.
 * 
 * \author Author Name <author@email.com>
 * 
 * \version X.Y.Z
 * 
 * \date YYYY/MM/DD
 * 
 * \defgroup group_name Group Name
 * \{
 */
```

At the end of the file, the following line must be included:

```
/** \} End of group_name group */
```

## Function Headings

Function must be catalogued in their heading according to the following format:

```
/**
 * \brief Briefing description of the function.
 *
 * \param[in] <argument_1> brief description of the parameter (one line).
 *
 * \param[in,out] <argument_2> brief description of the parameter (one line).
 *
 * \note If applicable, notes can be added.
 *
 * \return Brief description of what is returned by the function.
 */
```

## Prevent Multiple Inclusions

All header files should have preprocessor checking to prevent multiple inclusions:

```
#ifndef FILENAME_H_
#define FILENAME_H_

/* Source code */

#endif /* FILENAME_H_ */
```

The header file should have the minimum required #includes possible. If a file is included because it is required for the implementation of the source file, then that file should be included in the source file, not the header file.

## Commenting

* Function prototypes should always have a description.
* All data structures should have a description explaining what each of their members is used for.

Comments on source code should emphasize why the code is there. A programmer reading the code should understand what it does and why it is there.

## Variable Naming

All variables must be declared in lower case letters and separated by an underline character when have multiple words:

```
int variable_example = 0;
```

## Indentation

Any source file must be indented with **four spaces** instead of a single tab character. The text editors or IDEs must be configured for that.

## Coding Standards

The [JPL Institutional Coding Standard for the C Programming Language](https://yurichev.com/mirrors/C/JPL_Coding_Standard_C.pdf) is the preferable coding standard, it is based on the automotive standard [MISRA-C:2004](https://www.misra.org.uk/product/misra-c2004/) with some modifications and additional remarks.

## Git Flow

Git is used as the version control tool, not only for software development but also for hardware development and documentation writing. The used branches scheme is ilustraded in the figure below:

![git-flow](https://github.com/spacelab-ufsc/spacelab/blob/master/figures/git-flow.png)

There are few long-term branches designated to accommodate changes from each segment of the project, in which the "dev_[segment]" branches are used for the regular development, "dev" is used to stage periodic change packages, and "master" is the production branch. Then, after a reasonable amount of regular commits or finished features, the stage branch receives the merges from the development ones. The production branch only receives tested and stable merges from the stage branch. In order to avoid improper versioning, only the repository administrators have permissions to perform merges to the production branch, and, in general, a pull request is created, awaiting the other administrators' approval for a given release. New releases are just created when predefined goals are met, and if the current code presented in the master branch passes all the tests.
