Development
==============

IDE and editors
-----------------

- Suggested editors for OCaml development: Emacs, Vim, Visual Studio Code.

- Code completion, navigation, outline by `merlin
  <https://github.com/ocaml/merlin>`_ and `ocaml-lsp
  <https://github.com/ocaml/ocaml-lsp>`_.

  .. code-block:: sh

     opam install merlin ocaml-lsp-server

- Code auto-formatting and indentation: `ocamlformat
  <https://github.com/ocaml-ppx/ocamlformat>`_ and `ocp-indent
  <https://github.com/OCamlPro/ocp-indent>`_:

  .. code-block:: sh

     opam install ocamlformat ocp-indent

- If you are using Emacs, then consider checking out this `Spacemacs Starter Kit
  <https://github.com/taquangtrung/spacemacs-starter>`_, which is already
  pre-configured with `merlin`, `ocaml-lsp`, `ocamlformat`, `ocp-indent` to
  support OCaml development.

OCaml Programming Guidelines
-------------------------------

- Programming guidelines and coding standards can be referred to:
  + `OCaml programming guidelines
    <https://ocaml.org/learn/tutorials/guidelines.html>`_, from official
    OCamlwebsite.
  + `Real World Ocaml <https://dev.realworldocaml.org/index.html>`_ (free,
    online book).

- Indentation by `ocp-indent <https://github.com/OCamlPro/ocp-indent>`_ and
  follow the rules configured in in ``discover/.ocp-indent``.

- Code auto-formatting by `ocamlformat
  <https://github.com/ocaml-ppx/ocamlformat>`_:

  + Use ``janestreet`` style and additional settings in
    ``discover/.ocamlformat`` and ``discover/.ocamlformat-ignore``.

  + To disable ocamlformat for certain code, use ``[@@ocamlformat "disable"]``:

    .. code-block:: ocaml

       let do_not_touch (x : t) (y : t) (z : t) = [
         x; y; z
       ] [@@ocamlformat "disable"]

       type bound =
         | PInf (* positive infinity *)
         | NInf (* negative infinity *)
         | Int64 of int64 (* integer 64 bit *)
         | EInt of eint (* integer in 2-exponential representation *)
         | BInt of bint (* big integer *)
       [@@ocamlformat "disable"]

- Every module must be accompanied by an ``*.mli`` interface file.

- Some general rules to write concise and readable code:

  + Use 2-white-space indentation style.

  + No trailing whitespaces at the end of every lines.

  + Each code line is at most 80 columns.

  + Function and variable names follow: ``snake_case_naming_style``.

  + Module and signature names follow: (``CamelCaseNamingStyle``).

  + Comment a region: always comment each line separately.

    .. code-block:: ocaml

       (* let list_head (lst: 'a list) : 'a option = *)
       (*   match lst with *)
       (*   | [] -> None *)
       (*   | hd :: tl -> Some tl  *)

Autoformat project using Dune
--------------------------------

- Require ``ocamlformat`` to be installed and the configuration file
  ``.ocamlformat`` at the project's root directory.

  Install the newest ``ocamlformat`` from its GitHub development repository:

  .. code-block:: sh

     opam pin --dev-repo ocamlformat

- Formatting the project by running the following ``dune`` command:

  .. code-block:: sh

     # Format the source code and display the differences
     dune build @fmt

     # Replace the source files by the corrected versions.
     dune promote

  or just run ``make format`` from the root folder of the project.


- Read more at this `formatting project tutorial <https://dune.readthedocs.io/en/stable/formatting.html>`_.
