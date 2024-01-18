    Okay: import os\nimport sys\n\nimport six\n\nimport hacking
    Okay: import six\nimport znon_existent_package
    Okay: import os\nimport threading
    S366: import mock\nimport os
    S366: import hacking\nimport os
    S366: import hacking\nimport nonexistent
    S366: import hacking\nimport mock
    """
    if (noqa or blank_before > 0 or
            indent_level != previous_indent_level):
        return

    normalized_line = core.import_normalize(logical_line.strip()).split()
    normalized_previous = core.import_normalize(previous_logical.
                                                strip()).split()

    def compatible(previous, current):
        if previous == current:
            return True

    if normalized_line and normalized_line[0] == 'import':
        current_type = _get_import_type(normalized_line[1])
        if normalized_previous and normalized_previous[0] == 'import':
            previous_type = _get_import_type(normalized_previous[1])
            if not compatible(previous_type, current_type):
                yield(0, 'S366: imports not grouped correctly '
                      '(%s: %s, %s: %s)' %
                      (normalized_previous[1], previous_type,
                       normalized_line[1], current_type))
