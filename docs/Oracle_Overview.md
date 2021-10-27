#Oracle Overview


An Oracle acts as a bridge between Real World Data and Blockchains. It sends data from the outside world, such as the cost of the commodities in our protocol, to a blockchain. So based on this data, Oracle feeds the protocol with information that can trigger predefined actions to our Oracle.
The x/oracle module includes integration with Band Protocol, a separate blockchain to handle and relay information. Data can be sent to other blockchains via Cosmos’ Inter-Blockchain Communication (IBC) protocol for accessing the latest reported price for cAssets. Price quotes are kept up-to-date by oracle feeders and are tasked with periodically fetching exchange rates from reputable sources and reporting them to the protocol.
