This library aims to be used as a drop-in replacement to github.com/mcosta74/pgx-slog

As described in [discussion](https://github.com/jackc/pgx/issues/1582#issuecomment-1734571794), slog in standard package is expected to be natively integrated in https://github.com/jackc/pgx/ after go 1.21 is released.

also, since x/slog is a different package from standard log/slog package, [github.com/mcosta74/pgx-slog](adapter for x/slog) is not compatible with standard log/slog
