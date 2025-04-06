===============================
Migration Guide: cocotb v1.x → v2.x
===============================

The cocotb v2.x release introduces several breaking changes. This guide helps you migrate your existing cocotb testbenches and extensions to the new version.

Major Changes
=============

1. Native Python async coroutines

cocotb now uses native Python `async`/`await` syntax. The legacy `@cocotb.coroutine` decorator and `yield`-based coroutines have been removed.

**Before:**
.. code-block:: python

    @cocotb.coroutine
    def test_example(dut):
        yield Timer(10, units='ns')

**After:**
.. code-block:: python

    async def test_example(dut):
        await Timer(10, units='ns')

You must:
- Remove all `@cocotb.coroutine` decorators
- Change `def` to `async def`
- Replace `yield` with `await`

2. Deprecated APIs

Several internal APIs have been removed or renamed. For a complete list, refer to the `CHANGELOG` or release notes:

https://docs.cocotb.org/en/latest/release_notes.html
Add initial migration guide for cocotb v2.x


3. Manual Migration or Tooling Support

Some migration patterns are complex and may require manual intervention. A migration helper tool is under development (planned as a GSoC project) to automate many of these changes.

---

If you're unsure about any migration changes, feel free to ask in the cocotb community channels (Gitter/Discord).
