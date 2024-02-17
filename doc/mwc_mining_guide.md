# Overview #
This page is intended to be the mining guide for MWC. Since MWC is a fork of [Grin](https://github.com/mimblewimble/grin),
[Grin Miner](https://github.com/mimblewimble/grin-miner) can be used to mine MWC. Grin miner must be pointed at an
[MWC full node](https://github.com/whyproject/why-node). Grin supports two mining algorithms: C29 (ASIC resistant) and C31+
(ASIC friendly). MWC supports both of those algorithms as well, but on launch, we will support C29d (a variant of the C29
algorithm). Grin's mining algorithm allows for 90% of the block rewards to go to C29 miners initially and then gradually go
down to 0% C29 two years after its launch. Since we are launching one year later, we will start at 45% C29d and gradually go
to 0% one year after launch. This is intended to keep us inline with Grin. Grin launched with the intent of doing a hard fork
every 6 months. We want to avoid doing that so we are likely to keep the C29d algorithm for the duration of the year that C29
is supported. We do reserve the right to do a hard fork should asics become a problem, but 6 months after launch C29 will only
account for less than 25% of the network so we hope to avoid hard forks all together.

# Procedure to mine #

1.) Setup and install a grin miner: [Grin Miner](https://github.com/mimblewimble/grin-miner). You will need a GPU that has
at least 5.5 GB of VRAM to effectively mine on the network. There are many discussions about which miners are best for Grin
and they all apply equally to MWC since we use the same mining algorithm. Nvidia RTX 2070 Ti is a good GPU for mining C29d
and Nvidia RTX 2080 Ti is a good GPU for mining C31+, but there are many other options and C31 ASICs are on the horizon.

2.) Setup an MWC full node and wallet: [MWC full node](https://github.com/whyproject/why-node) and
[why-wallet](https://github.com/whyproject/why-wallet).

3.) Modify your why-node's why-server.toml file to enable stratum server (by default this file is in
~/.why/main/why-server.toml:
change:
enable_stratum_server = false
to:
enable_stratum_server = true
and restart the why-node.

4.) Start your why-wallet listener:

```# why-wallet listen```

5.) Modify your grin-miner.toml to point to your why-node:
stratum_server_addr = "127.0.0.1:3416" (that is the default port of the stratum server in the why-node)

6.) start mining:

```# grin-miner```

Note: you must be using either one of the C31 plugins or the C29d plugin. C29 will not work.

You are done and the block rewards will go to the why-wallet instance that you setup.

# Reward Schedule #

MWC has a different reward schedule from grin. Grin's block reward subsidy is 60 grins per block indefinitely. MWC's
block reward subsidy starts at 2.380952380 MWC per block and has a halving every 4 years. After 32 halvings, the reward
subsidy is 0 MWC.
