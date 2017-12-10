! Using the ```!$acc paralllel``` directive leads to a slow down of the code. Takes to 0.4683 seconds to process.
```
program main 
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

    ! Initialize part1 and part2 arrays with numders from 1 to 2359296
    do i = 1, Nsize  
        part1(i)  = i
    end do 

    do i = 1, Nsize  
        part2(i)  = i
    end do 
    
    ! Timing program run
    start_time = omp_get_wtime()
    
    !$acc parallel
    do i = 1, Nsize  
        answer(i) =  part1(i)  + part2(i) * 4
    end do 
    !$acc end parallel

    elapsed_time = omp_get_wtime() - start_time
    print *, 'Program run in ', elapsed_time, ' seconds'

    deallocate(part1, part2)
end program main


```
