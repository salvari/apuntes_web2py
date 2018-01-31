# Varios

## executeSql

Hay que estudiar esto con calma y aprender a usarlo con precisión:

~~~~
    coloc_node_orig = db(  (db.site.id == myid)
                         & (db.site.site_name == db.segment.origination_site_name)
                        ).select(db.segment.origination_node.with_alias('node'),
                                 distinct=True)
    coloc_node_dest = db(  (db.site.id == myid)
                         & (db.site.site_name == db.segment.destination_site_name)
                        ).select(db.segment.destination_node.with_alias('node'),
                                 distinct=True)

    sql = """
    SELECT origination_node AS node
      FROM site s,
           segment g
     WHERE s.id = {0}
       AND s.site_name = g.origination_site_name
    UNION
    SELECT destination_node AS node
      FROM site s,
           segment g
     WHERE s.id = {0}
       AND s.site_name = g.destination_site_name""".format(myid)

    coloc_nodes = db.executesql(sql, fields=[db.segment.origination_node], colnames=['node'], as_dict=False)

~~~~
