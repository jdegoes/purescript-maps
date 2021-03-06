# Module Documentation

## Module Data.Graph

### Types

    data Edge k where
      Edge :: k -> k -> Edge k

    data Graph k v where
      Graph :: [v] -> [Edge k] -> Graph k v

    data SCC v where
      AcyclicSCC :: v -> SCC v
      CyclicSCC :: [v] -> SCC v


### Type Class Instances

    instance eqSCC :: (Eq v) => Eq (SCC v)

    instance showSCC :: (Show v) => Show (SCC v)


### Values

    scc :: forall v. (Eq v, Ord v) => Graph v v -> [SCC v]

    scc' :: forall k v. (Eq k, Ord k) => (v -> k) -> (k -> v) -> Graph k v -> [SCC v]

    topSort :: forall v. (Eq v, Ord v) => Graph v v -> [v]

    topSort' :: forall k v. (Eq k, Ord k) => (v -> k) -> (k -> v) -> Graph k v -> [v]

    vertices :: forall v. SCC v -> [v]


## Module Data.Map

### Types

    data Map k v


### Type Class Instances

    instance eqMap :: (P.Eq k, P.Eq v) => P.Eq (Map k v)

    instance functorMap :: P.Functor (Map k)

    instance showMap :: (P.Show k, P.Show v) => P.Show (Map k v)


### Values

    alter :: forall k v. (P.Ord k) => (Maybe v -> Maybe v) -> k -> Map k v -> Map k v

    checkValid :: forall k v. Map k v -> Boolean

    delete :: forall k v. (P.Ord k) => k -> Map k v -> Map k v

    empty :: forall k v. Map k v

    fromList :: forall k v. (P.Ord k) => [Tuple k v] -> Map k v

    insert :: forall k v. (P.Ord k) => k -> v -> Map k v -> Map k v

    isEmpty :: forall k v. Map k v -> Boolean

    keys :: forall k v. Map k v -> [k]

    lookup :: forall k v. (P.Ord k) => k -> Map k v -> Maybe v

    map :: forall k a b. (a -> b) -> Map k a -> Map k b

    member :: forall k v. (P.Ord k) => k -> Map k v -> Boolean

    showTree :: forall k v. (P.Show k, P.Show v) => Map k v -> String

    singleton :: forall k v. k -> v -> Map k v

    toList :: forall k v. Map k v -> [Tuple k v]

    union :: forall k v. (P.Ord k) => Map k v -> Map k v -> Map k v

    unions :: forall k v. (P.Ord k) => [Map k v] -> Map k v

    update :: forall k v. (P.Ord k) => (v -> Maybe v) -> k -> Map k v -> Map k v

    values :: forall k v. Map k v -> [v]


## Module Data.Set

### Types

    data Set a


### Type Class Instances

    instance eqSet :: (P.Eq a) => P.Eq (Set a)

    instance showSet :: (P.Show a) => P.Show (Set a)


### Values

    checkValid :: forall a. Set a -> Boolean

    delete :: forall a. (P.Ord a) => a -> Set a -> Set a

    empty :: forall a. Set a

    fromList :: forall a. (P.Ord a) => [a] -> Set a

    insert :: forall a. (P.Ord a) => a -> Set a -> Set a

    isEmpty :: forall a. Set a -> Boolean

    member :: forall a. (P.Ord a) => a -> Set a -> Boolean

    singleton :: forall a. a -> Set a

    toList :: forall a. Set a -> [a]

    union :: forall a. (P.Ord a) => Set a -> Set a -> Set a

    unions :: forall a. (P.Ord a) => [Set a] -> Set a