function [X] = ThomasAlgorithm(A, f)
    [row col] = size(A);
    [row_f col_f] = size(f);

    if(row == col && row == row_f)
        gamma = [0; 0; 0; 0; 0]; alpha = [0; 0; 0; 0; 0]; beta = [0; 0; 0; 0; 0];
        a = [0; 0; 0; 0; 0]; b = [0; 0; 0; 0; 0]; c = [0; 0; 0; 0; 0];
        X = [0; 0; 0; 0; 0];
        
        %a, b, c values
        a(1) = 0; b(1) = A(1, 1); c(1) = A(1,2);
        for i = 2:(row-1)
            a(i) = A(i, i-1);
            b(i) = A(i, i);
            c(i) = A(i, i+1);
        end

        %forward run
        a(row) = A(row, col-1); b(row) = A(row, col); c(row) = 0;

        gamma(1) = b(1); alpha(1) = -c(1) / gamma(1); beta(1) = f(1) / gamma(1);
        for i = 2:(row-1)
            gamma(i) = b(i) + a(i) * alpha(i-1);
            alpha(i) = -c(i) /  gamma(i);
            beta(i) = (f(i) - a(i)*beta(i-1))/gamma(i);
        end
        gamma(row) = b(row) + a(row) * alpha(row-1);
        beta(row) = (f(row) - a(row) * beta(row-1))/gamma(row);

        %reverse run
        X(row) = beta(row);
        for i = (row-1):-1:1
            X(i) = alpha(i) * X(i+1) + beta(i);
        end
        
    else
        disp('Matrix A is not square or the number of columns of the A, f matrices does not match!!!');
        X = -1;
    end
end
