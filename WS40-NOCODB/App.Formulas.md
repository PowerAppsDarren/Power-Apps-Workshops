

```PowerFx

    //
    // This serves as an enumerated table ID values
    //
    fxNOCODB_IDs = {
        Model:              "m9of4cf87r0whtm", 
        Nationality:        "mb3vlkew87heisq", 
        WorldCity:          "miadv506jvw9yih", 
        Vehicle:            "mi3oujhil27hwow", 
        Customer:           "mpoxynqw5oz2yll"
    };

    //
    // Collection of all the tables we're interested in
    // hosted within NOCODB: https://powerappers.up.railway.app/
    //
    fxTableListing = [
        {
            ID: fxNOCODB_IDs.Model, 
            Name: "Model", 
            SortOrder: 1
        }, 
        {
            ID: fxNOCODB_IDs.Nationality,
            Name: "Nationality", 
            SortOrder: 2
        }, 
        {
            ID: fxNOCODB_IDs.WorldCity,
            Name: "WorldCity", 
            SortOrder: 3
        }, 
        {
            ID: fxNOCODB_IDs.Vehicle,
            Name: "Vehicle", 
            SortOrder: 4
        }, 
        {
            ID: fxNOCODB_IDs.Customer,
            Name: "Customer", 
            SortOrder: 5
        }
    ];

```
