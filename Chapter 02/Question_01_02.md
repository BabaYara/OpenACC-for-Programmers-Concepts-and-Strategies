! A sequential version of the problem run on the GPU. Takes around 0.0181 seconds to complete.
```
program main GPUsequential 
    use omp_lib
    implicit none 
    integer              :: i, Nsize
    real*8, allocatable  :: answer(:), part1(:), part2(:)
    double precision     :: start_time, elapsed_time

    ! Initialize variables  and allocate arrays 
    Nsize = 2359296
    allocate(part1(Nsize), part2(Nsize), answer(Nsize))
    part1 = 0
    part2 = 0

    ! Timing program run
    start_time = omp_get_wtime()

    ! Initialize part1 and part2 arrays with numders from 1 to 2359296
    !$acc loop seq
    do i = 1, Nsize  
        part1(i)  = i
    end do 

   !$acc loop seq
    do i = 1, Nsize  
        part2(i)  = i
    end do 

    !$acc loop seq
    do i = 1, Nsize  
        answer(i) =  part1(i)  + part2(i) * 4
    end do 

    elapsed_time = omp_get_wtime() - start_time
    print *, 'Program run in ', elapsed_time, ' seconds'

    deallocate(part1, part2)
end program main GPUsequential
```

