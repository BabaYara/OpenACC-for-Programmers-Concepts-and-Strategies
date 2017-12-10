! Version of problem in book takes about 0.3669 seconds to complete. 
```
program main 
    use omp_lib
    implicit none 
    integer              :: i, j, k, Isize, Jsize, Ksize
    real*8, allocatable  :: new_data(:,:,:), old_data(:,:,:)
    double precision     :: start_time, elapsed_time

    ! Initialize variables  and allocate arrays 
    Isize         = 8
    Jsize         = 320
    Ksize         = 320
    allocate(new_data(Isize, Jsize, Ksize))
    allocate(old_data(Isize, Jsize, Ksize))
    new_data = 0
    old_data = 0

    ! Initialize old_data array with 4
    do i = 1, Isize  
        do j = 1, Jsize
            do k = 1, Ksize
                old_data(i,j,k)  = 4
            end do
        end do
    end do 
    
    ! Timing program run
    start_time = omp_get_wtime()
    
    !$acc parallel loop
    do i = 1, Isize  
        do j = 1, Jsize
            do k = 1, Ksize
                new_data(i,j,k)  = (old_data(i,j,k)*2) + 4.3
            end do
        end do
    end do 
    !$acc end parallel loop

    elapsed_time = omp_get_wtime() - start_time
    print *, 'Program runs in ', elapsed_time, ' seconds'

    deallocate(new_data, old_data)
end program main
```
