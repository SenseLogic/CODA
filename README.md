![](LOGO/coda.png)

# Coda

Language-agnostic coding standard.

## Goals

Efficiently develop code and applications with the following qualities :

*   **Robust** : runs without crash and protects the data from being lost or corrupted.
*   **Secure** : protects the data from being stolen or hacked.
*   **Ergonomic** : does exactly what the user needs and can be used in a productive and intuitive manner.
*   **Efficient** : minimizes processing times to maximize the user productivity.
*   **Maintainable** : is easy to fix and enhance by any programmer in the team.
*   **Extensible** : is easy to extend with new features by reusing existing components.
*   **Consistent** : looks like it has been designed and implemented by a single developer.

## Specificity

This coding standard targets self-documenting code, and therefore favors readability over compactness by :

*   forbidding the use of cryptic acronyms, abbreviations, prefixes and suffixes;
*   using only letter cases to distinguish classes, class members and local variables;
*   including the class name in attributes and variable names.

## General rules

*   Develop the application and its components with simple, robust and efficient code which will be easy to understand, extend and debug by any programmer in the team.

*   Develop any piece of code so that it's :

    *   easy to understand just by itself;
    *   impossible to guess who has actually worked on it.

*   Use the concise functions provided by the high level libraries instead of calling directly the low level functions they wrap.

*   Use **American English** everywhere.

    ```cs
    InitializeColor();
    MoveForward();
    ```

*   Use the **English language order** in compound identifiers.

    ```cs
    enemy_list_by_category_dictionary = GetEnemyListByCategoryDictionary();
    ```

*   Use the **meter** as the default distance unit.

*   Use the **second** as the default time unit.

*   Use **four spaces** instead of tabulations, to make the code independent of the editor settings.

*   Use **Unix line endings**.

*   Trim **trailing whitespace** on save.

*   Choose **short meaningful identifiers** for class, attribute, method, constant and variable names, to prevent ambiguity and cognitive load.

*   Use **standard prefixes** :

    *   First, Last, Post
    *   Prior, Next
    *   Sub, Super, Base
    *   Initial, Final
    *   Old, New
    *   Backward, Forward
    *   Left, Right
    *   Back, Front
    *   Bottom, Top
    *   Minimum, Maximum
    *   Lower, Higher, Upper
    *   Horizontal, Vertical
    *   Local, Global

*   Use **standard suffixes** :

    *   Index, Count
    *   Array, List, Map, Dictionary

*   Use **standard verbs** :

    *   Initialize, Update, Finalize
    *   Create, Release, Destroy
    *   Build, Apply
    *   Clear, Fill
    *   Reset, Set, Get, Find
    *   Is, Has
    *   Add, Remove
    *   AddFirst, RemoveFirst
    *   AddLast, RemoveLast
    *   Start, Stop
    *   Begin, End
    *   Enter, Exit
    *   Open, Close
    *   Read, Write
    *   Load, Save
    *   Pause, Resume
    *   Lock, Unlock
    *   Attach, Detach
    *   Enable, Disable
    *   Select, Deselect
    *   Activate, Deactivate
    *   Increment, Decrement
    *   Increase, Decrease
    *   Compress, Decompress
    *   Connect, Disconnect
    *   Send, Receive
    *   Grant, Revoke

*   Name your **types** (classes, structures, enumerations, etc) in **UPPER_CASE**, without articles.

    ```cs
    class TANK_SHELL
    {
        VECTOR_3
            PositionVector;
        QUATERNION
            RotationQuaternion;

        ...
    }
    ```

*   Name your **type members** (methods, attributes, constants, etc) in **PascalCase**, without articles.

    ```cs
    ShootShell(
        Muzzle.PositionVector,
        Muzzle.RotationQuaternion
        );
    ```

*   Name your **local variables** and **method parameters** in **snake_case**, without articles.

    ```cs
    void ShootShell(
        VECTOR_3 shell_position_vector,
        QUATERNION shell_rotation_quaternion
        )
    {
        TANK_SHELL
            shot_tank_shell;

        ...

        shot_tank_shell
            = new TANK_SHELL(
                  shell_position_vector,
                  shell_rotation_quaternion
                  );

        ...
    }
    ```

*   Don't use abbreviations or single-letter variables.

    ```cs
    TANK FindTank(
        int tank_identifier,
        int first_tank_index,
        int post_tank_index
        )
    {
        int
            tank_index;

        for ( tank_index = first_tank_index;
              tank_index < post_tank_index;    // no i, j, n, etc
              ++tank_index )
        {
            if ( TankArray[ tank_index ].Identifier == tank_identifier )
            {
                return TankArray[ tank_index ];
            }
        }

        return null;
    }
    ```

*   Avoid acronyms, and capitalize them in member names.

    ```cs
    DATABASE_URL
        DatabaseUrl;
    ```

*   If a variable name collides with a predefined identifier, simply add a trailing underscore.

    ```cs
    CLASS
        class_;

    class_ = new CLASS();
    ```

*   Use a noun or noun phrase for classes, constants, attributes and variable names.

*   Include the meaningful part of the class name in attribute and variable names.

    ```cs
    Dictionary<string, PLAYER>
        ActivePlayerDictionary;
    List<ENEMY>
        CloseEnemyList;
    TANK[]
        EnemyTankArray;
    VECTOR_3
        InitialShellPositionVector,
        TankVelocityVector;

    void ShootShell(
        )
    {
        SHELL
            last_shot_shell,
            shot_shell;

        ...
    }
    ```

*   Start method names with a verb in the imperative mood (Set, Get, Find, ...).

*   Start boolean inquiry names with a verb in the indicative mood (Is, Has, Can, ...).

*   Declare the method parameters in the same order as in the method name.

    ```cs
    bool FindPlayerIndexByName(
        ref int player_index,
        string player_name
        )
    {
        ...
    }
    ```

*   Use a positive affirmation for boolean variable and attribute names.

    ```cs
    if ( game_is_paused )
    {
        ...
    }
    ```

*   If an attribute name starts like its owner class name, omit the common prefix.

    ```cs
    class TANK
    {
        TANK_SHELL[]
            ShellArray;
        bool
            IsDamaged;

        void ShootShell(
            TANK_SHELL tank_shell
            )
        {
            ...
        }
    }
    ```

*   Align matching braces.

    ```cs
    bool CanShoot(
        )
    {
        return ShotShellCount < MaximumShellCount;
    }

    // ~~

    void ShootShell(
        VECTOR_3 initial_velocity_vector
        )
    {
        ...
    }
    ```

*   Use braces for single statement blocks.

    ```cs
    if ( LoadedAmmunitionCount > 0 )
    {
        ShootBullet();
    }
    else if ( CarriedAmmunitionCount > 0 )
    {
        ReloadWeapon();
    }
    else
    {
        NoAmmunitionSound.Play();
    }
    ```

*   Declare each attribute, variable and method parameter name on a separate line.

    ```cs
    int
        tank_count,
        tank_index;
    ```

*   Try to declare all local variables at the start of the method, to improve the algorithm readability.

*   Group local variables of the same type, and sort the declarations by ascending types (lowercase, then PascalCase, then UPPER_CASE) and variable names, so that the declaration of a variable can be located at a glance.

    ```cs
    int
        shell_count,
        shell_index,
        tank_count,
        tank_index;
    string
        player_name,
        target_name;
    CharacterController
        character_controller;
    NavMeshAgent
        navigation_mesh_agent;
    TANK
        enemy_tank;
    TANK[]
        enemy_tank_array;
    ```

*   Split complex statements and expressions on several lines if they contain boolean operators or if they become too wide.

*   When splitting an expression on several lines, start the next lines with an operator and align it with the start of its left operand (or else indent it by 4 spaces).

    ```cs
    if ( ( tower.GetDistance(
               tower_target,
               weapon_type
               )
           > tower.MaximumShootingDistance )
         || ( tank_distance > maximum distance
              && tank_health > 0.5 ) )
    {
        ...
    }
    ```

*   Favor indexed iterations over foreach iterations, and foreach iterations over functional iterations.

    ```cs
    for ( enemy_index = 0;
          enemy_index < EnemyList.Count;
          ++enemy_index )
    {
        ...
    }

    foreach ( ENEMY enemy in EnemyList )
    {
        ...
    }
    ```

*   Put the scalar or constant multiplier after the multiplicand expression.

    ```cs
    average_value = ( first_value + second_value ) * 0.5f;
    ```

*   Add exactly one space :

    *   after `(` `[` `,`
    *   before `)` `]`
    *   after `if` `while` `for` `foreach` `return` ...
    *   around operators.

*   Add exactly one empty line :

    *   around standard comments;
    *   after the local variable declarations;
    *   after the method preconditions;
    *   between `if` `while` `for` `foreach` `do` `return` and the prior statement;
    *   between `}` and the next statement.

*   Use standard file extensions.

    *   C# : cs
    *   C : c, h
    *   C++ : cpp, hpp
    *   Javascript : js
    *   HTML : html
    *   CSS : css

*   Declare one class per source code file.

*   Use the class name in lowercase as file name.

    ```cs
    tank_shell.cpp
    tank_shell.hpp
    ```
*   Group the class elements by category, and declare them in this order :

    *   Imports.
    *   Types.
    *   Constants.
    *   Attributes.
    *   Constructors.
    *   Destructor.
    *   Operators.
    *   Inquiries : methods which don't change the class attributes.
    *   Operations : methods which may change the class attributes.

*   Within a category, declare :

    *    the called methods before the calling methods, preferably in the order they will be called, so that the class code can be immediately understood by a single sequential read.
    *    the static members after the non-static members.

*   Import exactly what each file needs to be compiled independently, and nothing more.

*   Sort the imports by ascending names.

*   Declare code sections in this order :
    *   imports
    *   constants
    *   types
    *   variables
    *   functions
    *   statements

*   Delimitate code sections with standard comments.

    ```cs
    // -- IMPORTS

    ...

    // -- CONSTANTS

    ...

    // -- TYPES

    class NAME
    {
        // -- CONSTANTS

        ...

        // -- ATTRIBUTES

        ...

        // -- CONSTRUCTORS

        ...

        // -- DESTRUCTOR

        ...

        // -- OPERATORS

        ...

        // -- INQUIRIES

        ...

        // -- OPERATIONS

        ...
    }

    // -- VARIABLES

    ...

    // -- FUNCTIONS

    ...

    // -- STATEMENTS

    ...
    ```

*   Don't use standard comments for empty sections.

*   Align multiple lines comments with the surrounding statements, start them with an uppercase character and end them with a period.

    ```cs
    /*
        A long explanation which must be written
        on several lines.
    */

    ...
    ```

*   Align single line comments with the surrounding statements, start them with an uppercase character and end them with a period.

    ```cs
    // A short explanation which can be written on a single line.

    ...
    ```

*   Put end of line comments exactly four spaces after the statement, and start them with lowercase character.

    ```cs
    DoSomethingWeird();    // a short explanation
    ```

*   Name the unit test class by simply adding a `_TEST` suffix to the class name.

## C++ rules

*   Begin header files with `#pragma once`.

    ```cs
    #pragma once

    // -- IMPORTS

    #include "tank.hpp"
    #include "tank_shell.hpp"

    // -- TYPES

    ...
    ```

## CSS rules

*   Use double quotes for string literals.

*   Name your **ids** and **classes** in **kebab-case**, without articles.

*   Use :
    *   **unitless** values for line heights.
    *   **rem** values for font sizes and all other static sizes.
    *   **px** values only for tiny static sizes, like 1 or 2 pixels.
    *   **%**, **vh**, **vw**, **vmin** and **vmax** values for dynamic sizes.
    *   zero or one decimal in your sizes (0.9rem, 1.2vh), unless you absolutely need more precision (0.75rem, 1.25rem).

*   Group **rules** by category, and declare them in this order :

    *   Imports
    *   Constants
    *   Variables
    *   Functions
    *   Mixins
    *   Fonts
    *   Elements
    *   Classes

*   Delimitate rule sections with standard comments.

    ```cs
    // -- IMPORTS

    ...

    // -- CONSTANTS

    ...

    // -- VARIABLES

    ...

    // -- FUNCTIONS

    ...

    // -- MIXINS

    ...

    // -- FONTS

    ...

    // -- ELEMENTS

    ...

    // -- CLASSES

    ...
    ```

*   Order **rules** by increasing interiority, appearance order, and specificity.

*   For a same base selector class, declare rules in this order :

    *   @keyframe class-animation
    *   .class
    *   .class:not()
    *   .class:first-child
    *   .class:nth-child()
    *   .class:last-child
    *   .class:hover
    *   .class:focus
    *   .class:active
    *   .class:invalid
    *   .class:before
    *   .class:after
    *   .class:placeholder-shown
    *   .class::placeholder
    *   .class ~ .other-class
    *   .class + .other-class
    *   .class > .other-class
    *   .class .other-class
    *   .class#id
    *   .class.other-class

*   Declare concatenated **specifiers** in this order :

    *   element
    *   #id
    *   .class
    *   :not()
    *   :first-child
    *   :nth-child()
    *   :last-child
    *   :hover
    *   :focus
    *   :active
    *   :invalid
    *   :before
    *   :after
    *   :placeholder-shown
    *   ::placeholder

*   Declare **media queries** inside the rule using the "+Media" mixin, right after the declarations, and order them by increasing breakpoint.

    ```css
    .class
    {
        ...

        +Media( min-width-40em )
        {
            ...
        }

        +Media( min-width-60em )
        {
            ...
        }

        +Media( min-width-80em, max-height-40em )
        {
            ...
        }

        +Media( "min-width-80em && max-height-40em" )
        {
            ...
        }

        +Media( "min-width-80em && min-height-40em", "max-width-120em && min-height-60em" )
        {
            ...
        }

        +Media( "min-width-80em && min-height-40em", "max-width-120em && min-height-60em" )
        {
            ...
        }
    }
    ```

*   Group **declarations** by category :

    *   Inheritance
    *   Position
    *   Container
    *   Layout
    *   Content
    *   Typography
    *   Behavior

*   Delimitate declaration sections with a blank line.

    ```css
    .header-menu
    {
        z-index: 100;
        position: fixed;
        top: 0;
        left: 0;
        right: 0;

        padding: 1rem;

        display: flex;
        justify-content: center;
        align-items: center;

        background-color: transparent;

        transition: background-color 0.3s ease;

        +Media( min-width-40em )
        {
            padding: 2rem;
        }

        +Media( min-width-60em )
        {
            padding: 3rem;
        }
    }
    ```

*   Declare **properties** in this order :

    *   Inheritance
        *   @extend
    *   Position
        *   z-index
        *   position
        *   top
        *   bottom
        *   left
        *   right
        *   transform
    *   Container
        *   overflow
        *   overflow-y
        *   overflow-x
        *   box-sizing
        *   scrollbar-width
        *   inset
        *   margin
        *   margin-block
        *   margin-block-start
        *   margin-block-end
        *   margin-inline
        *   margin-inline-start
        *   margin-inline-end
        *   margin-top
        *   margin-bottom
        *   margin-left
        *   margin-right
        *   outline
        *   height
        *   min-height
        *   max-height
        *   width
        *   min-width
        *   max-width
        *   aspect-ratio
        *   border
        *   border-top
        *   border-bottom
        *   border-left
        *   border-right
        *   border-width
        *   border-style
        *   border-color
        *   border-image
        *   border-radius
        *   border-top-radius
        *   border-top-left-radius
        *   border-top-right-radius
        *   border-bottom-radius
        *   border-bottom-left-radius
        *   border-bottom-right-radius
        *   border-collapse
        *   padding
        *   padding-top
        *   padding-bottom
        *   padding-left
        *   padding-right
    *   Layout
        *   display
        *   flex
        *   flex-direction
        *   flex-wrap
        *   flex-grow
        *   flex-shrink
        *   flex-basis
        *   flex-flow
        *   grid-template
        *   grid-template-rows
        *   grid-template-columns
        *   grid-template-areas
        *   grid-auto-rows
        *   grid-gap
        *   gap
        *   row-gap
        *   column-gap
        *   grid-area
        *   grid-row
        *   grid-column
        *   justify-content
        *   justify-items
        *   justify-self
        *   align-content
        *   align-items
        *   align-self
        *   order
        *   float
        *   clear
        *   columns
        *   column-count
        *   column-width
        *   column-span
        *   column-fill
        *   column-gap
        *   column-rule
        *   column-rule-width
        *   column-rule-style
        *   column-rule-color
        *   shape-outside
        *   clip-path
        *   object-fit
    *   Content
        *   content
        *   visibility
        *   opacity
        *   background
        *   background-clip
        *   background-color
        *   background-image
        *   background-origin
        *   background-position
        *   background-repeat
        *   background-size
        *   background-attachment
        *   box-shadow
        *   filter
        *   backdrop-filter
    *   Typography
        *   list-style-type
        *   direction
        *   writing-mode
        *   text-orientation
        *   line-height
        *   font
        *   font-family
        *   font-size
        *   font-weight
        *   font-style
        *   font-stretch
        *   font-variant
        *   white-space
        *   overflow-wrap
        *   word-wrap
        *   word-break
        *   word-spacing
        *   letter-spacing
        *   caption-side
        *   vertical-align
        *   text-align
        *   text-align-last
        *   text-indent
        *   text-justify
        *   text-overflow
        *   text-decoration
        *   text-decoration-line
        *   text-decoration-style
        *   text-decoration-color
        *   text-transform
        *   text-shadow
        *   color
    *   Behavior
        *   resize
        *   scroll-behavior
        *   scroll-snap-type
        *   scroll-snap-points-y
        *   scroll-snap-points-x
        *   user-select
        *   pointer-events
        *   cursor
        *   transition
        *   transition-property
        *   transition-delay
        *   transition-duration
        *   transition-timing-function
        *   animation
        *   animation-name
        *   animation-delay
        *   animation-duration
        *   animation-timing-function
        *   animation-iteration-count
        *   animation-direction
        *   animation-fill-mode
        *   animation-play-state
    *   Media queries (of increasing breakpoint size)

*   Declare Stylus constants in **PascalCase**.

    ```css
    RedColor = #F87272;
    RedColor100 = darken( RedColor, 80% );
    ```

*   SCSS constants in **kebab-case**.

    ```css
    $red-color: #F87272;
    $red-color-100: mix( $red-color, #000000, 80% );
    ```

## HTML rules

*   Use double quotes for string literals.

*   Use single quotes inside double-quoted string literals.

*   Declare tag **attributes** in this order :

    *   id
    *   class sorted by increasing specificity
    *   style sorted as explained above
    *   data-* in alphabetical order
    *   tag-specific attributes (src, href, etc) in alphabetical order
    *   on* in alphabetical order

    ```html
    <div id="header-menu-home-button"
         class="button scaled-button header-menu-button header-menu-home-button"
         style="margin-left: auto; background-image: url( '/static/image/header_menu/home_button.svg' )"
         data-view-name="home"
         onclick="ShowView( 'home' )">
        ...
    </div>
    ```

## Phoenix rules

*   Use the component name in lowercase as file name.

    ```php
    header_menu.pht
    ```

*   Declare component sections in this order :

    *   shared style
    *   inline style
    *   HTML template
    *   shared script
    *   inline script

*   Prefix all **classes** by the component name in **kebab-case**, and **child** classes by their **parent** class name.

    ```php
    <style file="header_menu.styl">
        .header-menu
        {
            ...
        }

        .header-menu-button-container
        {
            ...
        }

        .header-menu-button
        {
            ...
        }

        .header-menu-button:hover,
        .header-menu-button.is-selected
        {
            ...
        }

        .header-menu-button-image
        {
            ...
        }

        .header-menu-button-text
        {
            ...
        }

        ...
    </style>
    <style>
        ...
    </style>
    <div id="header-menu" class="header-menu">
        <div class="header-menu-button-container"
            <div class="header-menu-button" data-view-name="home" onclick="ShowView( 'home' )">
                <img class="header-menu-button-image" src="/static/image/header_menu/home_button.svg"/>
                <span class="header-menu-button-text">
                    <# .GetText( 'HeaderMenuHomeButton' ) #>
                </span>
            </div>
            <div class="header-menu-button" data-view-name="contact" onclick="HandleHeaderMenuButtonClickEvent( event.currentTarget )">
                <img class="header-menu-button-image" src="/static/image/header_menu/contact_button.svg"/>
                <span class="header-menu-button-text">
                    <# .GetText( 'HeaderMenuContactButton' ) #>
                </span>
            </div>
            ...
        </div>
    </div>
    <script file="header_menu.js">
        // -- FUNCTIONS

        function HandleHeaderMenuButtonClickEvent(
            header_menu_button_element
            )
        {
            ShowView( header_menu_button_element.dataset.viewName );
        }
    </script>
    <script>
        ...
    </script>
    ```

## Unity rules

*   Use the class name in uppercase as Unity file name.

    ```cs
    TANK_SHELL.cs
    ```

*   To be consistent with existing assets, name your scene assets and files in **PascalCase**.

## JavaScript rules

*   To be consistent with existing libraries, when using front-side rendering libraries like Svelte, React or Kwik :
    *   name types and file names in **PascalCase**;
    *   name type members, function parameters and local variables in **camelCase**.

## Guidelines

*   **Design before you program** by quickly writing :

    *   a short text or UI flow explaining how to use the application, to optimize the **application interface** before implementing it;
    *   a short text explaining what the application components will do, to optimize the **application architecture** before implementing it;
    *   a short text or test code demonstrating how to use the application components, to optimize the **component interface** before implementing it.

*   Develop programs **gradually**, one feature at a time, using **simple** and **efficient** code.

*   Don't overgineer your code, choose **simple modular designs** which can easily be extended.

*   Don't repeat yourself, create **reusable components** that you can use across one or several projects.

*   Be a source of **order**, not of chaos. So even if you are on a hurry, continue to develop **clean maintainable code**, this is will actually allow you to **ship faster**.

*   Instead of adding comments to explain the code intent, **refactor the code** to make it obvious by :

    *   using **clearer names** for the classes, attributes, functions, parameters and variables;
    *   using local variables to store **intermediate results**;
    *   splitting long functions into several **smaller functions** called in sequence;
    *   keeping your functions small enough so that they **just do what their name says**, and nothing more.

*   Develop "**baby code**" that looks so simple and obvious that even a child could quickly understand what it does.

*   When you see **design or implementation flaws**, correct them immediately. If you put them off, they will eventually build up and slow you down in the future,
    so always leave the code in a better state than you found it.

*   Make the application **resilient** to external conditions (network failures, missing or corrupted files, etc).

*   Check invalid method parameters with **assertions** in the debug build.

*   For performance reasons, preferably use :

    *   public attributes without getters and setters.
    *   public non-virtual methods.
    *   virtual methods instead of delegates.
    *   state classes instead of coroutines.

*   Create automated **unit tests**.

*   Only **stable tested code** can be pushed under source control, so always **test your changes** extensively before pushing them.
    .
## Version

1.2

## Author

Eric Pelzer (ecstatic.coder@gmail.com).

## License

This project is licensed under the GNU Lesser General Public License version 3.

See the [LICENSE.md](LICENSE.md) file for details.
