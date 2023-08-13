# Summary

AssetRegistry is a place where all YieldBox controlled assets are registered.

For each asset registration, four information should be supplied.
    - TokenType tokenType(ERC20, ERC721, ERC1155)
    - address contractAddress
    - IStrategy strategy
    - uint256 tokenId

It will allocate new asset id only increasing.

# Checklists
- [ ] Registrer/Unregister Asset
- [ ] Set Operator Approval For Given Asset
