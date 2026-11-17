:tocdepth: 2

.. meta::
   :description: Answers to common SpeedCrunch questions about installation, calculations, precision, units, sessions, customization and troubleshooting.

.. _faq:

Frequently Asked Questions
==========================

This page answers the questions that SpeedCrunch users ask most often.
For more detail, see the :doc:`userguide/index`. You can also open the manual
in the app by pressing **F1**, or choosing **Help → User Manual**.

.. note::

   On macOS, use **Cmd** where this page says **Ctrl**.

.. contents:: Questions
   :local:
   :depth: 2
   :backlinks: none


General
-------

.. _faq-what-is-speedcrunch:

What is SpeedCrunch?
~~~~~~~~~~~~~~~~~~~~

SpeedCrunch is a fast, high-precision scientific calculator for your desktop.
You type a whole expression on the keyboard and press **Enter**. It shows the
result and keeps a full history of your work.

.. _faq-is-it-free:

Is it free?
~~~~~~~~~~~

Yes. SpeedCrunch is free and open source, under the GNU GPL version 2.
There are no ads and no paid features.

.. _faq-supported-systems:

Which systems does it run on?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- **Windows:** 64-bit Windows 10 (version 1809 or later) or Windows 11
- **macOS:** macOS 14.4 (Sonoma) or later
- **Linux:** most distributions, with X11 or Wayland

.. _faq-language:

Is it available in my language?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Probably. SpeedCrunch is translated into more than 40 languages. Change it in
**Settings → Language**.

.. _faq-limitations:

What can SpeedCrunch NOT do?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SpeedCrunch is a calculator, not a full math program. It does not draw graphs,
solve equations, or do symbolic algebra (for example, derivatives or
integrals in symbolic form).


Installation and updates
------------------------

.. _faq-installation:

How do I install SpeedCrunch?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Download it from `speedcrunch.org <https://speedcrunch.org>`_.

- **Windows:** use the installer, or the portable ``.zip`` version.
- **macOS:** open the disk image and drag SpeedCrunch to **Applications**.
- **Linux:** install it from your distribution (for example
  ``sudo apt-get install speedcrunch`` or ``sudo dnf install speedcrunch``), or
  from `Flathub <https://flathub.org/apps/org.speedcrunch.SpeedCrunch>`_.

.. _faq-portable-version:

What is the portable version?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

It is a Windows version that needs no installation. Unzip it and run
``speedcrunch.exe``. It saves all settings and data in its own folder, so you can
copy it to a USB stick and use it on another computer.

.. _faq-macos-unverified-developer:

macOS says it "cannot verify the developer". What do I do?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Only continue if you downloaded SpeedCrunch from the official website.

1. Try to open SpeedCrunch once.
2. Open **System Settings → Privacy & Security**.
3. Under **Security**, click **Open Anyway** next to SpeedCrunch.
4. Confirm. macOS remembers your choice.

.. _faq-older-windows:

I use Windows 7 or 8. Can I still use SpeedCrunch?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Not the current version. Use SpeedCrunch 0.12 from the "Older Versions" part
of the `download page <https://www.speedcrunch.org/download.html>`__.

.. _faq-updates:

How do I get updates?
~~~~~~~~~~~~~~~~~~~~~

Official builds check for updates automatically, at most once a week. You can
also check yourself with **Help → Check for Updates**. On Linux, your package
manager or Flathub usually handles updates.


Basic calculations
------------------

.. _faq-enter-calculation:

How do I calculate something?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Type the expression and press **Enter**. For example:

.. parsed-literal::

   ``54*(4.514 - 5.7)``
   ``= -64.044``

.. _faq-function-arguments:

Why do I get an error when I use a comma between function arguments?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SpeedCrunch uses a **semicolon** (``;``) to separate arguments, not a comma:

.. parsed-literal::

   ``average(12; 34; 56)``
   ``= 34``

The comma can be a decimal separator, so it cannot also separate arguments.

.. _faq-previous-result:

How do I use the previous result?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use ``ans``. It always holds the last result:

.. parsed-literal::

   ``2+3``
   ``= 5``
   ``7*ans``
   ``= 35``

**Tip:** If you start a new line with an operator such as ``+``, ``-``, ``*`` or ``/``,
SpeedCrunch adds ``ans`` for you. Type ``+3`` and you get ``ans+3``.

.. _faq-recall-calculation:

How do I recall an earlier expression or result?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- Press **Up** and **Down** in the input field to go through earlier
  expressions.
- Double-click any line in the result area to copy it into the input field.

.. _faq-implicit-multiplication:

Why is ``6/2(2+1)`` equal to 9 and not 1?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Implicit multiplication (no ``*`` sign) has the same priority as ``*`` and ``/``.
SpeedCrunch works from left to right: ``6/2 = 3``, then ``3*(2+1) = 9``.
The result area shows how SpeedCrunch read your expression, so you can always
check it. Use parentheses if you mean something else: ``6/(2(2+1))``.

.. _faq-power-associativity:

Why is ``2^2^3`` equal to 256?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Powers are calculated from right to left: ``2^(2^3) = 2^8 = 256``.

.. _faq-percent:

How does percent work?
~~~~~~~~~~~~~~~~~~~~~~

``%`` divides by 100. With ``+`` and ``-``, the percentage is taken from the number
on the left:

.. parsed-literal::

   ``1000 + 12%   = 1120``
   ``1000 - 12%   = 880``
   ``1000 * 12%   = 120``

.. _faq-comments:

How do I write a comment?
~~~~~~~~~~~~~~~~~~~~~~~~~

Use a question mark. Everything after ``?`` is ignored:

.. parsed-literal::

   ``1 + 2 ? simple sum``
   ``? this whole line is a comment``

.. _faq-large-and-small-numbers:

How do I enter very large or very small numbers?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use ``e`` for "times 10 to the power of": ``1.234e-9`` means ``1.234 × 10⁻⁹``.
SpeedCrunch accepts huge exponents, like ``1e+500000000``, without overflow.


Results, precision and number formats
-------------------------------------

.. _faq-precision:

How precise is SpeedCrunch?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

It stores about 78 significant digits for each number. This is much more than
most calculators. You can show up to 50 decimal places.

.. _faq-decimal-places:

How do I change the number of decimal places?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the **precision selector** in the status bar (**View → Status Bar**, or
**Ctrl+B**), or **Settings → Results → Notation & Precision...**.

.. _faq-fractions:

How do I get results as fractions?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Choose **Rational** notation in the status bar or in
**Settings → Results → Notation & Precision...**. Or use ``rat()`` for a single
result:

.. parsed-literal::

   ``rat(0.75)``
   ``= 3/4``

In Rational mode, common trigonometric results are shown in exact form, such
as ``pi/2`` or ``√(2)/2``.

.. _faq-notation:

How do I switch between scientific, engineering and other formats?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the notation selector in the status bar, or the function keys:

.. list-table::
   :header-rows: 1
   :widths: 10 90

   * - Key
     - Notation
   * - F2
     - Automatic decimal
   * - F3
     - Fixed-point decimal
   * - F4
     - Engineering
   * - F5
     - Scientific
   * - F7
     - Octal
   * - F8
     - Hexadecimal
   * - F9
     - Sexagesimal (degrees/time with minutes and seconds)
   * - F10
     - Binary

To format only one result, use ``sci()``, ``eng()``, ``hex()``, ``bin()``, ``oct()`` or
``dec()``.

.. _faq-extra-result-lines:

Can I see the same result in two formats at once, for example decimal and hex?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Open **Settings → Results → Notation & Precision...** and turn on one or
more of the four extra result lines. Each line can have its own notation and
number of decimal places.

.. _faq-decimal-separator:

My computer uses a comma as the decimal separator. Does that work?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. When you type, SpeedCrunch accepts both a dot and a comma as the decimal
point. To choose how results look (decimal mark and digit grouping), use
**Settings → Number Format...**.

.. _faq-trailing-zeroes:

How do I stop showing extra zeros, like ``3.140``?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Turn on **Settings → Results → Remove Trailing Zeroes**.

.. _faq-rounding:

Can I choose how results are rounded?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, in **Settings → Results → Rounding Mode**. You can choose normal
rounding, banker's rounding, truncation, round up or round down. This only
changes how results look. To round a value inside a calculation, use
``round()``, ``roundeven()``, ``trunc()``, ``ceil()`` or ``floor()``.


Variables, functions and units
------------------------------

.. _faq-variables:

How do I save a value in a variable?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use ``name = value``:

.. parsed-literal::

   ``mass = 120``
   ``g = 9.81``
   ``weight = mass*g``
   ``= 1177.2``

You can add a description with ``?``: ``g = 9.81 ? gravity``.

.. _faq-custom-functions:

How do I create my own function?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. parsed-literal::

   ``f(x) = 5*x + 8``
   ``f(5)``
   ``= 33``

For more parameters, use semicolons: ``f(x; y) = x*y + x``.

.. _faq-delete-definitions:

How do I delete a variable or function?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open the **User Variables** (**Ctrl+4**) or **User Functions** (**Ctrl+5**)
panel. Select the item and press **Delete**, or use the right-click menu.

.. _faq-global-definitions:

Can I have variables and functions in every session automatically?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Put them in **Settings → User Definitions...**, one per line. They are
loaded into every session. Click **Validate** to test them and **Apply** to use
them.

.. _faq-enter-units:

How do I use units?
~~~~~~~~~~~~~~~~~~~

Put units in square brackets after a number:

.. parsed-literal::

   ``5[ft]``
   ``= 1.524 m``

.. _faq-unit-brackets:

Why do units need square brackets?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In version 0.12, units were plain names, like variables. This caused
problems:

- **Name clashes.** Every SI prefix could go with every unit, so many short
  names were already taken, for example ``mg``, ``cm``, ``ms``, ``ns``, ``pm``, ``Pa`` and
  ``kt``. Few short names were left for your own variables.
- **No standard symbols.** Many units had to use English names, like
  ``second``. With brackets, you can write standard symbols, like ``[s]``, ``[m]``
  and ``[km/h]``.
- **No real unit system.** Now units are a separate thing, not just
  variables.
- **Mixed suggestions.** Autocomplete showed units together with functions
  and variables. Now, inside ``[ ]``, it suggests only units.
- **No custom units.** With brackets, you can create your own units, like
  ``[mpg]`` (see :ref:`faq-custom-units`).

With brackets, names like ``a``, ``l``, ``m`` and ``mg`` are free again for your own
variables.

.. _faq-faster-unit-entry:

Typing brackets is slow. Can I make it faster?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, a few things help:

- Type ``[`` and SpeedCrunch adds the ``]`` for you at the end of the expression.
- Inside brackets, autocomplete suggests unit names. Press **Tab** to accept.
- Write a whole unit in one bracket: ``[km/h]`` instead of ``[km]/[h]``.
- Add a button that inserts ``[`` to a custom keypad
  (**Settings → Edit Custom Keypad...**).

.. _faq-units-without-brackets:

Can I turn the brackets off and use the old 0.12 style?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No, there is no option for this. But you can get close with your own
variables. Open **Settings → User Definitions...** and add the units you use
often, one per line:

.. parsed-literal::

   ``km = 1[km]``
   ``h = 1[h]``
   ``kg = 1[kg]``

Now ``100 km / (2 h)`` works without brackets. Results are shown in SI units,
so this gives ``13.8888… m/s``. To get another unit, you still need brackets
for the conversion target: ``100 km / (2 h) -> [km/h]`` gives ``50 km/h``.

If you really prefer the old style, SpeedCrunch 0.12 is still in the
"Older Versions" part of the
`download page <https://www.speedcrunch.org/download.html>`__. But it will not get
new features or fixes.

.. _faq-unit-conversion:

How do I convert between units?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use ``->`` or ``in``:

.. parsed-literal::

   ``10[kn] -> [km/h]``
   ``= 18.52 km/h``

   ``77[°F] in [°C]``
   ``= 25 °C``

.. _faq-incompatible-units:

Why do I get an error when I convert seconds to meters?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SpeedCrunch checks dimensions. Time and length cannot be converted into each
other, so it shows an error. This protects you from mistakes.

.. _faq-square-units:

How do I square a value with a unit?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Put the value and the unit in parentheses: ``(2[m])^2``. To enter two square
meters, write ``2[m^2]``. SpeedCrunch rejects ``2[m]^2`` because it is not clear.

.. _faq-custom-units:

Can I create my own units?
~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Put the new name in brackets on the left:

.. parsed-literal::

   ``[earth_radius] = 6371[km]``
   ``1[au] in [earth_radius]``

This is very useful for units that SpeedCrunch does not have. For example, to
convert car fuel use from miles per gallon to liters per 100 km:

.. parsed-literal::

   ``[mpg] = 1[mi/gal_us]``
   ``[L100km] = 1[L] / 100[km]``
   ``1 / (40[mpg]) -> [L100km]``
   ``= 5.88036458333333333333 L100km``

To keep your units in every session, add them to
**Settings → User Definitions...**.

.. _faq-unit-list:

Where can I find the list of units?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See the :doc:`units reference <reference/units>`. Unit names use
American English and the singular form, for example ``meter`` and ``foot``.


Advanced math
-------------

.. _faq-angle-mode:

How do I switch between degrees and radians?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the angle selector in the status bar, or **Settings → Angle Mode**. You can
also write the unit in the expression. Then the angle mode does not matter:

.. parsed-literal::

   ``cos(180[deg])``
   ``= -1``

.. _faq-complex-numbers:

Does SpeedCrunch support complex numbers?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, always. Use ``i`` or ``j``:

.. parsed-literal::

   ``(5+3j)/(8-2j)``
   ``= 0.5+0.5j``

Note: ``5j`` means ``5*j``, but ``j5`` is a variable name. You can change the
symbol and the display form (rectangular, polar, and so on) in
**Settings → Results**.

.. _faq-negative-roots:

Why is ``(-8)^(1/3)`` a complex number and not -2?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Fractional powers give the principal complex root. For a real root, use
``cbrt(-8) = -2``, or ``root(3; -8) = -2``.

.. _faq-number-bases:

How do I use binary, octal and hexadecimal numbers?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use a prefix: ``0b`` for binary, ``0o`` for octal, and ``0x`` or ``#`` for hex:

.. parsed-literal::

   ``0xFF + 0b101``
   ``= 260``
   ``hex(255)``
   ``= 0xFF``

Bitwise operators also work: ``&`` (and), ``|`` (or), ``~`` (not), ``<<`` and ``>>``
(shifts). The **Bit Field** panel (**Ctrl+8**) lets you click single bits.

.. _faq-twos-complement:

Why is ``bin(-1)`` shown as ``-0b1`` and not as all ones?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SpeedCrunch shows the sign and the value separately. It does not use two's
complement. Use ``mask()`` to get the two's complement form, for example
``mask(-1; 8)``.

.. _faq-time-and-angles:

Can I calculate with time and angles in minutes and seconds?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Use ``:`` for time and ``°`` for angles. Minutes can be more than 60:

.. parsed-literal::

   ``12:90``
   ``= 13:30:00``

**Tip:** Type ``@`` to get the ``°`` sign.

.. _faq-statistics:

Does it have statistics functions?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, for example ``average``, ``median``, ``stdevs``, ``stdevp``, ``vars``, ``ncr``,
``npr``, ``binompmf`` and ``poicdf``. To sum an expression, use ``summation``:

.. parsed-literal::

   ``summation(1; 10; 2+n)``
   ``= 75``

.. _faq-lists-and-matrices:

Can I work with lists and matrices?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Use braces and semicolons:

.. parsed-literal::

   ``det({{1; 2}; {3; 4}})``
   ``= -2``
   ``{1; 2; 3} + {4; 5; 6}``
   ``= {5; 7; 9}``

Other functions include ``dot``, ``cross``, ``inv``, ``transpose`` and ``rank``.

.. _faq-special-functions:

What other special functions are there?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A few examples:

- ``molmass(C6H12O6)`` gives the molar mass of a chemical formula.
- ``datetime()`` and ``epoch()`` convert between Unix time and dates.
- ``ieee754_double_encode()`` and similar functions show how computers store
  floating-point numbers.
- ``randint(1; 6)`` gives a random whole number.

Open the **Functions** panel (**Ctrl+3**) to see all of them.

.. _faq-constants:

Where do I find scientific constants?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Press **Ctrl+K** and type a name, like ``speed of light``. Press **Enter** to
insert it. You can also open the **Constants** panel (**Ctrl+2**). Common
constants like ``pi`` and ``e`` are always available by name.


History and sessions
--------------------

.. _faq-automatic-session-saving:

Is my work saved when I close the app?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. SpeedCrunch saves your sessions automatically. When you start it again,
your windows, tabs and history come back.

.. _faq-edit-calculation:

Can I fix a mistake in an earlier calculation?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Move the mouse over the calculation and click the edit icon. Change the
expression and confirm. SpeedCrunch then recalculates every line below it.
(Hover highlighting must be on: **Settings → Appearance → Hover
Highlighting**.)

.. _faq-clear-history:

How do I clear the history?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Press **Ctrl+L**, or use **Edit → Clear History**. Your variables and functions
stay. To remove everything in the session, including variables, use
**Session → Reset**.

.. _faq-tabs-and-splits:

Can I use several calculations side by side?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes.

- **Ctrl+T** opens a new tab.
- **View → Split** shows two or more sessions next to each other.
- **Session → New Window** opens a new window.

You can drag tabs between panes and windows.

.. _faq-private-tabs:

What is a private tab?
~~~~~~~~~~~~~~~~~~~~~~

A private tab is not saved to disk. When you close it, its content is gone.
Open one with **Ctrl+Shift+N**. To keep it after all, choose **Session → Keep**.

.. _faq-reopen-tab:

I closed a tab by mistake. Can I get it back?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Press **Ctrl+Shift+T** or use **Session → Reopen Closed Tab**. (This does
not work for private tabs.)

.. _faq-history-limit:

How many lines does the history keep?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Up to 1000 per session by default. When the history is full, the oldest lines
are removed. Change the limit in **Session → History Size Limit...**. Use ``0``
for no limit.

.. _faq-export-calculations:

How do I save, share or print my calculations?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use **Session → Export**:

- **HTML** keeps the colors. Open it in a browser to print it. A light theme
  is best for printing.
- **Plain text** works everywhere.
- **JSON** is for importing back into SpeedCrunch with **Session → Import**.

.. _faq-session-files:

Where are my session files stored?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use **Session → Open Sessions Folder**. This is useful for backups.


Customizing the app
-------------------

.. _faq-colors:

How do I change the colors?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Open **Settings → Appearance → Theme...**. Choose a light or dark theme, or
change single colors to make your own. You can import and export themes as
JSON files.

.. _faq-style-presets:

SpeedCrunch looks different from older versions. Can I get the old look back?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Use **Settings → Appearance → Style Presets**:

- **Classic** looks similar to version 0.12 and uses your system style.
- **Modern** uses the SpeedCrunch theme everywhere.
- **Hybrid** is like Classic, but the panels use the SpeedCrunch theme.

.. _faq-text-size:

How do I make the text bigger or smaller?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Hold **Ctrl** and turn the mouse wheel, or press **Shift+Up** and
**Shift+Down**. To choose a different font, use
**Settings → Appearance → Input and Results → Font...**.

.. _faq-show-keypad:

How do I show or hide the on-screen keypad?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use **View → Keypad**. You can choose Basic, Scientific (wide), Scientific
(narrow), Custom, or Disable. Change the keypad size with
**Settings → Appearance → Keypad → Zoom**.

.. _faq-custom-keypad:

Can I design my own keypad?
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Choose **Settings → Edit Custom Keypad...**. Set the number of rows and
columns, then choose what each button does. You can start from one of the built-in
layouts. Click **OK** to save and use the layout. Later, choose
**View → Keypad → Custom** to select it again.

.. _faq-keyboard-shortcuts:

Can I change keyboard shortcuts?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes, since version 1.2. Open **Settings → Keyboard Shortcuts**, click the box
next to an action, and press the new keys.

.. _faq-always-on-top:

How do I keep SpeedCrunch on top of other windows?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Turn on **Settings → Window → Always on Top**. This option is not available on
Linux with Wayland.

.. _faq-window-opacity:

Can I make the window see-through?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yes. Hold **Ctrl+Shift** and turn the mouse wheel.

.. _faq-menu-bar:

Can I hide the menu bar?
~~~~~~~~~~~~~~~~~~~~~~~~

On Windows and Linux, yes: **View → Main Menu**. You can still reach the menu
by right-clicking the result area. On macOS, the menu bar belongs to the
system, so you cannot hide it.

.. _faq-subsequent-launch:

What happens when I start SpeedCrunch while it is already running?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

By default, it brings the open window to the front. You can change this in
**Settings → Window → On Subsequent Launch**, to open a new window or a new
tab instead.

.. _faq-reset-settings:

How do I go back to the default settings?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use **Settings → Reset All Settings...**. Your history, sessions and user
definitions are not deleted.


Tips and tricks
---------------

- **Autocomplete:** Start typing a function or variable name and press **Tab**
  to complete it.
- **Function help:** Put the cursor on a function name and press **F1** to open
  its manual page.
- **Parameter hints:** While you type a function, SpeedCrunch shows its
  parameters and highlights the current one.
- **Live preview:** You see the result while you type. Select part of an
  expression to see the result of only that part.
- **Copy the last result:** Press **Ctrl+R**. To copy every new result
  automatically, turn on **Settings → Results → Copy New Results Automatically**.
- **Wrap in parentheses:** Select part of the expression and press **Ctrl+(**.
  With no selection, the whole expression is wrapped.
- **Formula Book:** Press **Ctrl+1** for ready-made formulas from algebra,
  geometry, electronics and radio frequency.
- **Keep the expression:** Turn on **Settings → Editing → Keep Expression After
  Evaluation** to change and re-run the same expression quickly.
- **Clear with Escape:** Turn on **Settings → Editing → Escape Clears Editor**.
- **Paste many lines:** Paste several lines at once and each line is
  calculated.
- **Readable numbers:** You can type ``1 000 000`` or ``1_000_000``. The spaces and
  underscores are ignored.
- **Copy a whole calculation:** Right-click a calculation and choose
  **Copy → Calculation as Single Line**, for example ``120 / 8 = 15``.
- **Powers made easy:** ``**`` works like ``^``, so ``2**10 = 1024``.
- **Full screen:** Press **F11**.
- **Keyboard only:** Press **F6** to move between the input field and the
  panels without a mouse.


Problems and help
-----------------

.. _faq-input-adjustments:

Some characters change when I type them. How do I stop this?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

SpeedCrunch adjusts your input, for example it adds closing brackets and turns
``*`` into ``×``. To type exactly what you want, turn off
**Settings → Editing → Automatic Input Adjustments**.

.. _faq-arrow-key-history:

The Up and Down keys move through history, but I want to move the cursor.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Change **Settings → Editing → Up/Down Arrow History** to **Never** or
**Only for Single-Line Expressions**.

.. _faq-constants-shortcut:

Ctrl+K does nothing.
~~~~~~~~~~~~~~~~~~~~

Another program may use this shortcut. Choose a different key for
**Search Constants** in **Settings → Keyboard Shortcuts**.

.. _faq-report-problem:

I found a bug or I have an idea. Where do I report it?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Use the `issue tracker <https://speedcrunch.org/issues.html>`_. Please include
the report from **Help → App Diagnostics**. Click **Copy to Clipboard** and
paste it into your issue. You can also ask there for new formulas in the
Formula Book.
