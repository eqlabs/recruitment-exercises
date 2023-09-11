# van Emde Boas map

Spec v1 (2022-04-29)

van Emde Boas tree (https://en.wikipedia.org/wiki/Van_Emde_Boas_tree) is a data structure for fast (logarithmic in the number of bits) lookup of integer keys. Implement it as a specialization of C++ map for some integer type.

## Requirements

- Do not halve the key all the way to 1 bit - switch to flat map on byte level. Bonus points for demonstrating if/when that's too small and the switch should occur at multiple bytes.

- Note any part of std::map interface that cannot be (efficiently) implemented.

- Include unit tests.

## Checklist

- The above invites implementation for uint16_t (or int16_t). 32 bits may take too much space (practical implementations I've seen used space optimizations at that level), larger types almost certainly do.

- I'm not aware of any part of std::map that couldn't be implemented with this, but I didn't read the latest reference.
