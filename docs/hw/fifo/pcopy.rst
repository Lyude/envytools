.. _pcopy:
.. _pcopy-falcon:
.. _pcopy-io:
.. _pcopy-mmio:
.. _pcopy-intr:

====================
PCOPY copying engine
====================

Present on:
    cv0 [1 engine]: GT215:GF100

    cv1 [2 engines]: GF100:GK104

    cv2 [3 engines]: GK104+
BAR0 address:
    engine #0: 0x104000

    engine #1: 0x105000

    engine #2: 0x105000
PMC interrupt line:
    cv0: 22

    cv1, engine #0: 5

    cv1, engine #1: 6
PMC enable bit:
    cv0: 13

    cv1, engine #0: 6

    cv1, engine #0: 7
Version:
    cv0, cv1: 3

    cv2: [none]
Code segment size:
    0x1200
Data segment size:
    0x800
Fifo size:
    0x10
Xfer slots:
    8
Secretful:
    no
Code TLB index bits:
    cv0: 5

    cv1: 7
Code ports:
    1
Data ports:
    1
IO addressing type:
    indexed
Core clock:
    cv0: NVCLK

    cv1: hub clock [Fermi clock #9]
Tesla VM engine:
    0xd
Tesla VM client:
    0x13
Tesla context DMA:
    0xc
Fermi VM engine:
    engine #0: 0x15

    engine #1: 0x16

    engine #2: 0x1b
Fermi VM client:
    engine #0: HUB 0x01

    engine #1: HUB 0x02

    engine #2: HUB 0x18

The IO registers:

    ============ =============== =========== ===========
    Host         Falcon          Name        Description
    ============ =============== =========== ===========
    0x600:0x640  0x18000:0x19000 MEMIF       :ref:`Falcon memory interface<falcon-memif>`
    0x640:0x680  0x19000:0x1a000 ???         ??? :ref:`pcopy`
    0x800:0x880  0x20000:0x22000 COPY        :ref:`Copy engine<pcopy>`
    0x900:0x980  0x24000:0x26000 ???         ??? :ref:`pcopy`
    ============ =============== =========== ===========

Interrupts:
    ===== ===== ==================== ===============
    Line  Type  Name                 Description
    ===== ===== ==================== ===============
    8     edge  MEMIF_TARGET_INVALID [GT215:GF100] :ref:`MEMIF port not initialised <falcon-memif-intr-port-invalid>`
    9     edge  MEMIF_FAULT          [GT215:GF100] :ref:`MEMIF VM fault <falcon-memif-intr-fault>`
    9     edge  MEMIF_BREAK          [GF100-] :ref:`MEMIF Break <falcon-memif-intr-break>`
    10    level COPY_BLOCK
    11    level COPY_NONBLOCK
    ===== ===== ==================== ===============

Status bits:
    ==== ======= ===========
    Bit  Name    Description
    ==== ======= ===========
    0    FALCON  :ref:`Falcon unit <falcon-proc>`
    1    MEMIF   :ref:`Memory interface <falcon-memif>` and :ref:`COPY <pcopy>`
    ==== ======= ===========

.. space:: 8 pcopy 0x1000 memory copy engine

   .. todo:: write me

.. todo:: describe PCOPY
