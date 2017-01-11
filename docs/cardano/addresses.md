# Addresses in Cardano SL

To send and receive value, Addresses are used in virtually any cryptocurrency.

## How Does an Address Look Like?

```
type AddressHash = AbstractHash Blake2s_224

unsafeAddressHash :: Bi a => a -> AddressHash b
unsafeAddressHash = AbstractHash . secondHash . firstHash
  where
    firstHash :: Bi a => a -> Digest SHA3_256
    firstHash = hashlazy . Bi.encode
    secondHash :: Digest SHA3_256 -> Digest Blake2s_224
    secondHash = CryptoHash.hash

addressHash :: Bi a => a -> AddressHash a
addressHash = unsafeAddressHash
```

## Public Key Addresses

_Pending_

## Pay to Script Hash

_Pending_
