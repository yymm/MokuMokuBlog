:title: Rust - よく戻り値で使われる core::result 
:date: 2014-12-15 05:43:45
:tags: Rust

`core::result - Rust <http://doc.rust-lang.org/core/result/>`_

matchで受けるような設計になっている。

.. code-block:: rust

 match res {
     Ok(t) => println!("OK: {}", t),
     Err(e) => println!("Err: {}", e),
 }

FileIOのWriteなどもこの戻り値になっている。いろんなところで使われているEnum。
