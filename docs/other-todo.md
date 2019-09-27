---
title: Other - Todo
sidebar_label: "Other: Todo"
---

AKA the junk drawer of todos. Still very important to do, but hard to organize. Sam just puts thoughts in here on what eventually needs to get done.

## Montage

1. Montage VM setup docs
2. is_contaminated field in production Montage

## Bit.IO

1. Properly set up Spectrum instance
   - NOTE: Weird double dependency bug that is fixed by linking, but this is fairly manual process.
2. Add components to bit
3. Ensure examples are correct
4. Document

## Loader

### Loading Data

1. Collaborator data into separate Montage instances
2. New Cellmine data
   1. Need to collect appropriate metadata for it

### New Montage loader (by Andrew + crew)

Eventually need to swap Oleg's loader with this one.

Development is currently not managed by us, although a lot of the work overlaps with efforts we're making for Alhena and Mira. So need to get a better handle on what they've been adding and see whether we can merge that with our work.

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
It would be good to have a dedicate domain stuff for all viz stuff. Especially as we deploy other things through production. Also having separate links for staging and what not would be super valuable.