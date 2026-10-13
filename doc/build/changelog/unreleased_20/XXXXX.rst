.. change::
    :tags: bug, orm
    :tickets: XXXXX
    :versions: 2.1.5

    Fixed regression caused by :ticket:`11917` where an ORM-enabled
    :func:`_sql.update` with WHERE criteria, using the "evaluate" or "fetch"
    synchronization strategies, would expire server-side onupdate columns, as
    well as columns given a SQL expression in the SET clause, on only one of
    the matched objects in the :class:`_orm.Session`, rather than on all of
    them.  The remaining objects would silently retain their previous values,
    or report ``None`` for attributes that were not yet loaded.
