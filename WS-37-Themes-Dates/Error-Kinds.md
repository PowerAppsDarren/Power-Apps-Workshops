# Error-Kinds

In case you need to swap out an Error Code with a KindName.

```PowerFx
    fxErrorKinds = [
        {KindNumber: 0, KindName: "None"},
        {KindNumber: 1, KindName: "Unknown"},
        {KindNumber: 2, KindName: "InvalidArgument"},
        {KindNumber: 3, KindName: "NotFound"},
        {KindNumber: 4, KindName: "PermissionDenied"},
        {KindNumber: 5, KindName: "Timeout"},
        {KindNumber: 6, KindName: "ConcurrencyConflict"},
        {KindNumber: 7, KindName: "RateLimitExceeded"},
        {KindNumber: 8, KindName: "OperationCancelled"},
        {KindNumber: 9, KindName: "QuotaExceeded"},
        {KindNumber: 1, KindName: "Sync"},
        {KindNumber: 2, KindName: "MissingRequired"},
        {KindNumber: 3, KindName: "CreatePermission"},
        {KindNumber: 4, KindName: "EditPermissions"},
        {KindNumber: 5, KindName: "DeletePermissions"},
        {KindNumber: 6, KindName: "Conflict"},
        {KindNumber: 8, KindName: "ConstraintViolated"},
        {KindNumber: 9, KindName: "GeneratedValue"},
        {KindNumber: 10, KindName: "ReadOnlyValue"},
        {KindNumber: 11, KindName: "Validation"},
        {KindNumber: 13, KindName: "Div0"},
        {KindNumber: 14, KindName: "BadLanguageCode"},
        {KindNumber: 15, KindName: "BadRegex"},
        {KindNumber: 16, KindName: "InvalidFunctionUsage"},
        {KindNumber: 17, KindName: "FileNotFound"},
        {KindNumber: 18, KindName: "AnalysisError"},
        {KindNumber: 19, KindName: "ReadPermission"},
        {KindNumber: 20, KindName: "NotSupported"},
        {KindNumber: 21, KindName: "InsufficientMemory"},
        {KindNumber: 23, KindName: "Network"},
        {KindNumber: 24, KindName: "Numeric"}
    ];
```