# Source Architecture
What are some decisions that must be considered when thinking about how to organize our project?
    - One unified API
    - Independent allocators each with their own API

Since we are going to use a benchmarking system, then the cleanest option would be: One unified API

Why is one unified API better in this case? We won't have to modify our benchmarks or create custom versions per allocator. Instead, we will be able to run any benchmark with any allocator creating an abstraction of the allocators implementation.


