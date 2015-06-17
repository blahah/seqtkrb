# seqtkrb

seqtkrb is a ruby gem that wraps [seqtk](). This gives you fast access to basic operations on FASTA/FASTQ files without having to roll your own C extension or write a slow implementation in ruby.

Currently only the sampling functionality of seqtk is exposed. Create an issue or a Pull Request if you want more functionality.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'seqtkrb'
```

And then execute:

```
$ bundle
```

Or install it yourself as:

```
$ gem install seqtkrb
```

## Usage

```ruby
require 'seqtkrb'

seqtk = SeqTK.new # will download and install seqtk if it is not found

# basic sampling
seqtk.sample('reads.fq', 10_000) # sample 10,000 reads
seqtk.sample('reads.fq', 0.5) # sample reads with 50% chance of taking each read

# sampling from paired files
seqtk.sample('reads_l.fq', 1_000, 1234) # sample 1,000 left reads with seed 1234
seqtk.sample('reads_r.fq', 1_000, 1234) # sample the matching right reads

# low memory sampling (uses two passes)
seqtk.sample_lowmem('reads.fq', 1_000_000) # sample 1 million reads

```

## Contributing

1. Fork it ( https://github.com/[my-github-username]/seqtkrb/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request