! A sequential version of the problem run on the CPU to access accurate value.
```
program main 
    use omp_lib
    implicit none 
    integer              :: i, Nsize, passing_count
    real*8, allocatable  :: moving(:), left(:), right(:)
    double precision     :: start_time, elapsed_time

    ! Initialize variables  and allocate arrays 
    Nsize         = 10000
    passing_count = 0
    allocate(moving(Nsize), left(Nsize), right(Nsize))
    moving = 0
    left   = 0
    moving = 0

    ! Initialize moving, left and right arrays with numders from 1 to Nsize
    do i = 1, Nsize  
        moving(i)  = i
    end do 

    do i = 1, Nsize  
        left(i)  = i
    end do 

    do i = 1, Nsize  
        right(i)  = i
    end do 
    
    ! Timing program run
    start_time = omp_get_wtime()
    
    do i = 1, Nsize
        moving(i)     = (left(i)  - right(i)) * 2  
        left(i)       =  left(i)  + 0.6
        right(i)      =  right(i) - 3
        passing_count = passing_count + 1
    end do 

    elapsed_time = omp_get_wtime() - start_time
    print *, 'Program runs in ', elapsed_time, ' seconds'
    print *, 'Last element in passing_count', passing_count

    deallocate(moving, left, right)
end program main
```
