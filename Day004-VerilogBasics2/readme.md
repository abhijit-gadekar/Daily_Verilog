# 📘 Chapter 4: Basics of Verilog
---

## 📝 4.1: Lexical Conventions in Verilog

- The basic lexical conventions used by Verilog HDL are similar to those in the C programming language.
- Verilog contains a stream of tokens. Tokens can be comments, delimiters, numbers, strings, identifiers, and keywords.
- Verilog HDL is a case-sensitive language.
- All keywords are in lowercase. 

### 4.1.1: Whitespace

  - Blank spaces (\b) , tabs (\t) and newlines (\n) comprise the whitespace.
  - Whitespace is ignored by Verilog except when it separates tokens.

        assigny=1'b1;    // ❌ Invalid — 'assigny' is not a recognized keyword
        assign y = 1'b1; // ✅ Valid — whitespace separates 'assign' and 'y'
    
        So here, whitespace is required to separate the keyword assign from the signal name y.
    
  - Whitespace is not ignored in strings.
  - Whitespace has no effect on functionality.

 ### 4.1.2: Comments
 
  - Comments can be inserted in the code for readability and documentation.
  - There are two ways to write comments. A one-line comment starts with "//".
  - Verilog skips from that point to the end of line. A multiple-line comment starts with "/*" and ends with "*/".
  - Multiple-line comments cannot be nested.

         a = b && c; // This is a one-line comment
        /* This is a multiple line
        comment */
        /* This is /* an illegal */ comment */ 

### 4.1.3: Operators

  - Operators are of three types, unary, binary, and ternary.
    1. Unary operators precede the operand.
    2. Binary operators appear between two operands.
    3. Ternary operators have two separate operators that separate three operands.

            a = - b; // - is a unary operator. b is the operand
            a = b && c; // && is a binary operator. b and c are operands
            a = b ? c : d; // ?: is a ternary operator. b, c and d are operands

  i. Arithmetic Operators
  
  <div align="center">
    <img src="https://github.com/user-attachments/assets/adfcf64d-d188-4b24-b569-5b55f5ab30cc" width="500">
  </div>

  Example:

    module arithmetic_operators();
    initial begin
        $display (" 5  +  10 = %d", 5  + 10);
        $display (" 5  -  10 = %d", 5  - 10);
        $display (" 10 -  5  = %d", 10 - 5);
        $display (" 10 *  5  = %d", 10 * 5);
        $display (" 10 /  5  = %d", 10 / 5);
        $display (" 10 /  -5 = %d", 10 / -5);
        $display (" 10 %s  3  = %d","%", 10 % 3);
        $display (" +5 = %d", +5);
        display (" -5 = %d", -5);
        #10  $finish;
    end
    endmodule

  Output:

    5  +  10 =  15
    5  -  10 =  -5
    10 -  5  =   5
    10 *  5  =  50
    10 /  5  =  2
    10 /  -5 = -2
    10 %  3  =   1
    +5 =  5
    -5 =  -5
  
  ii. Relational Operators

  <div align="center">
    <img src="https://github.com/user-attachments/assets/a5414515-f222-41ff-9321-8ed5bec0802e" width="500">
  </div>

  Example:
  
    module relational_operators();
    initial begin
       $display (" 5     <=  10 = %b", (5     <= 10));
       $display (" 5     >=  10 = %b", (5     >= 10));
       $display (" 1'bx  <=  10 = %b", (1'bx  <= 10));
       $display (" 1'bz  <=  10 = %b", (1'bz  <= 10));  
       #10  $finish;
    end 
    endmodule

  Output:

    5     <=  10 = 1
    5     >=  10 = 0
    1'bx  <=  10 = x
    1'bz  <=  10 = x

  iii. Equality Operators

  <div align="center">
    <img src="https://github.com/user-attachments/assets/9d7d5bd4-f9dd-41f6-ab7b-f731f5bb7c0f" width="500">
  </div>

  Example:

    module equality_operators(); 
    initial begin
       // Case Equality
       $display (" 4'bx001 ===  4'bx001 = %b", (4'bx001 ===  4'bx001));
       $display (" 4'bx0x1 ===  4'bx001 = %b", (4'bx0x1 ===  4'bx001));
       $display (" 4'bz0x1 ===  4'bz0x1 = %b", (4'bz0x1 ===  4'bz0x1));
       $display (" 4'bz0x1 ===  4'bz001 = %b", (4'bz0x1 ===  4'bz001));
       // Case Inequality
       $display (" 4'bx0x1 !==  4'bx001 = %b", (4'bx0x1  ! ==  4'bx001));
       $display (" 4'bz0x1 !==  4'bz001 = %b", (4'bz0x1  ! ==  4'bz001));  
       // Logical Equality
       $display (" 5       ==   10      = %b", (5       ==   10));
       $display (" 5       ==   5       = %b", (5       ==   5));
       // Logical Inequality
       $display (" 5       !=   5       = %b", (5        ! =   5));
       $display (" 5       !=   6       = %b", (5        ! =   6));
       #10  $finish;
     end 
     endmodule
  
  Output:

    4'bx001 ===  4'bx001 = 1
    4'bx0x1 ===  4'bx001 = 0
    4'bz0x1 ===  4'bz0x1 = 1
    4'bz0x1 ===  4'bz001 = 0
    4'bx0x1 !==  4'bx001 = 1
    4'bz0x1 !==  4'bz001 = 1
    5       ==   10      = 0
    5       ==   5       = 1
    5       !=   5       = 0
    5       !=   6       = 1
 
  iii. Logical Operators

  <div align="center">
    <img src="https://github.com/user-attachments/assets/be867d47-4154-42ee-b8e5-d7a2ebf39944" width="500">
  </div>

  Example:
  
     module logical_operators();
     initial begin
        // Logical AND
        $display ("1'b1 && 1'b1 = %b", (1'b1 && 1'b1));
        $display ("1'b1 && 1'b0 = %b", (1'b1 && 1'b0));
        $display ("1'b1 && 1'bx = %b", (1'b1 && 1'bx));
        // Logical OR
        $display ("1'b1 || 1'b0 = %b", (1'b1 || 1'b0));
        $display ("1'b0 || 1'b0 = %b", (1'b0 || 1'b0));
        $display ("1'b0 || 1'bx = %b", (1'b0 || 1'bx));
       // Logical Negation
       $display ("! 1'b1       = %b", ( !   1'b1));
       $display ("! 1'b0       = %b", ( !   1'b0));
       #10  $finish;
    end 
    18 endmodule

  Output:
 
     1'b1 && 1'b1 = 1
     1'b1 && 1'b0 = 0
     1'b1 && 1'bx = x
     1'b1 || 1'b0 = 1
     1'b0 || 1'b0 = 0
     1'b0 || 1'bx = x
     ! 1'b1       = 0
     ! 1'b0       = 1

  iv. Bitwise Operators

  <div align="center">
    <img src="https://github.com/user-attachments/assets/c7a6c284-84d2-44b2-abb6-f8a22e379a17" width="700">
  </div>

  <div align="center">
    <img src="https://github.com/user-attachments/assets/4ab81d49-352a-4002-8b67-e7612e261adc" width="800">
  </div>

  Example:

    module bitwise_operators(); 
    initial begin
      // Bit Wise Negation
      $display (" ~4'b0001 = %b", (~4'b0001));
      $display (" ~4'bx001 = %b", (~4'bx001));
      $display (" ~4'bz001 = %b", (~4'bz001));
      // Bit Wise AND
      $display (" 4'b0001 &  4'b1001 = %b", (4'b0001 &  4'b1001));
      $display (" 4'b1001 &  4'bx001 = %b", (4'b1001 &  4'bx001));
      $display (" 4'b1001 &  4'bz001 = %b", (4'b1001 &  4'bz001));
      // Bit Wise OR
      $display (" 4'b0001 |  4'b1001 = %b", (4'b0001 |  4'b1001));
      $display (" 4'b0001 |  4'bx001 = %b", (4'b0001 |  4'bx001));
      $display (" 4'b0001 |  4'bz001 = %b", (4'b0001 |  4'bz001));
      // Bit Wise XOR
      $display (" 4'b0001 ^  4'b1001 = %b", (4'b0001 ^  4'b1001));
      $display (" 4'b0001 ^  4'bx001 = %b", (4'b0001 ^  4'bx001));
      $display (" 4'b0001 ^  4'bz001 = %b", (4'b0001 ^  4'bz001));
      // Bit Wise XNOR
      $display (" 4'b0001 ~^ 4'b1001 = %b", (4'b0001 ~^ 4'b1001));
      $display (" 4'b0001 ~^ 4'bx001 = %b", (4'b0001 ~^ 4'bx001));
      $display (" 4'b0001 ~^ 4'bz001 = %b", (4'b0001 ~^ 4'bz001));
       #10  $finish;
    end  
    endmodule

  Output:

    ~4'b0001           = 1110
    ~4'bx001           = x110
    ~4'bz001           = x110
    4'b0001 &  4'b1001 = 0001
    4'b1001 &  4'bx001 = x001
    4'b1001 &  4'bz001 = x001
    4'b0001 |  4'b1001 = 1001
    4'b0001 |  4'bx001 = x001
    4'b0001 |  4'bz001 = x001
    4'b0001 ^  4'b1001 = 1000
    4'b0001 ^  4'bx001 = x000
    4'b0001 ^  4'bz001 = x000
    4'b0001 ~^ 4'b1001 = 0111
    4'b0001 ~^ 4'bx001 = x111
    4'b0001 ~^ 4'bz001 = x111

