This library aims to be used as a drop-in replacement to github.com/mcosta74/pgx-slog

As described in [discussion](https://github.com/jackc/pgx/issues/1582#issuecomment-1734571794), slog in standard package is expected to be natively integrated in https://github.com/jackc/pgx/ after go 1.21 is released.

also, since x/slog is a different package from standard log/slog package, [github.com/mcosta74/pgx-slog](adapter for x/slog) is not compatible with standard log/slog

# usage

```

import (
	"context"
	"fmt"
	"log/slog"

	"github.com/jackc/pgx/v5/pgxpool"
	pgxslog "github.com/timtoronto634/pgx-slog"
)

func setupDB(logger *slog.Logger) (*pgxpool.Pool, error) {
	connStr := fmt.Sprintf(
		"postgres://%s:%s@%s:%d/%s?sslmode=disable",
		DBUser, DBPass, DBHost, DBPort, DBName,
	)
	config, err := pgxpool.ParseConfig(connStr)
	if err != nil {
		return nil, err
	}

	config.ConnConfig.Tracer = pgxslog.NewTracer(logger)
	return pgxpool.NewWithConfig(context.Background(), config)
}

```