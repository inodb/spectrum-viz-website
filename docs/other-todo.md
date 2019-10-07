---
title: Other - Todo
sidebar_label: "Other: Todo"
---

AKA the junk drawer of todos. Still very important to do, but hard to organize. Sam just puts thoughts in here on what eventually needs to get done.

## Montage

1. is_contaminated field in production Montage
   - NOTE: Currently waiting for reload of current data before we can propogate it to prod

## Bit.IO

1. Properly set up Spectrum instance
   - NOTE: Weird double dependency bug that is fixed by linking, but this is fairly manual process.
2. Add components to bit
3. Ensure examples are correct
4. Document

## Loader

### Loading Data

1. Collaborator data into separate Montage instances
   1. Data is still being loaded
   2. Set up webserver + certificates for instances to redirect to different subdomains
2. Cellmine
   - NOTE: Everything is currently loaded, but is just awaiting some checking and minor cleanup.

### New Montage loader (by Andrew + crew)

Eventually need to swap Oleg's loader with this one.

Development is currently not managed by us, although a lot of the work overlaps with efforts we're making for Alhena and Mira. So need to get a better handle on what they've been adding and see whether we can merge that with our work.

Arfath and Spencer are currently undergoing a redesign of all the work that has been done in an effort to further emcompass future data types, and to be maintainable. TBD on the exact details of this.

### Clean up loader files

I think I still have one repo for mira-db -- need to remove that to reduce confusion.

### Scaling

Want to parallelize loading. Tried with generators and processes but there's a lock-thread issue. Diljot suggested looking into kafka or rabbitmq

## Azure

1. Shut down unneeded VMs
2. Put auto-shutdown on staging ones
   1. Set up restarting docker containers when VMs are started

## Testing

Desperately want to add testing on all levels.

1. Want to take Javascript testing workshop: https://testingjavascript.com/

### Add tests for all projects

1. Alhena

   1. ETL (python part)
   2. GraphQL (resolvers)
   3. React

2. Hydra

   1. GraphQL (resolvers)
   2. React

3. Mira

   1. ETL (python part)
   2. GraphQL (resolvers)
   3. React

4. Sylph
   1. GraphQL (resolvers)
   2. React

## Domain name

We have bought a domain name and would like to set things up properly?

1. Link staging instances through there
