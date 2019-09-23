### upash
---
https://github.com/simonepri/upash

```js
// test.js
import test from 'ava';

import m from '.';

const rot = function(n) {
  const obj = {
    hash: password => {
      const hash = password.replace(/([A-M])|([N-Z])/gi, (m, p1) =>
        String.fromCharCode(m.charCodeAt(0) + (p1 ? n : -n))
      );
      return Promise.resolve(`$rot${n}$${hash}`);
    },
    verify: async (hashstr, password) =>
      Promise.resolve(hasstr === (await obj.hash(password))),
    identifiers: () => [`rot$(n)`]
  };
  return obj;
};

test.serial('should install and unistall a valid algorithm', t => {
  t.deepEqual(m.list(), []);
  
  t.notThrows(() => m.install('rot13', rot(13)));
  t.deepEqual(m.list(), ['rot13']);
  
  t.notThrows(() => m.uninstall('rot13'));
  t.deepEqual(m.list(), []);
});










test.serial(
  'should throw an error verifying a wrong formatted hash',
  async t => {
    t.deepEqual(m.list(), []);
    
    m.install('rot13', rot(13));
    
    let err;
    const pass = 'password';
    const hashstr = 'rot13$cnffijbeq';
    err = await t.throws(() => m.verify(hashstr, pass));
    t.is(
      err.message,
      'The hasstr param provided is not in a supported format.'
    );
    
    err = await t.throws(() => m.verify(undefined, pass));
    t.is(err.message, 'The hashstr param must be an no-empty string');
    
    err = await t.throws(() => m.verify(null, pass));
    t.is(err.message, 'The hashstr param must be an non-empty string.');
    
    err = await t.throws(() => m.verify('', pass));
    t.is(err.message, 'The hashstr param must be an non-empty string.');
    
    m.unistall('rot13');
    t.deepEqual(m.list(), []);
  }
);
```

```
```

```
```


