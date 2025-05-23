def process_file():
    # Ask the user for the input filename
    input_filename = input("Please enter the input filename to read: ")
    output_filename = "output_" + input_filename  # Create output filename dynamically
    
    try:
        # Attempt to open and read the input file
        with open(input_filename, 'r') as input_file:
            content = input_file.readlines()
            print("Input file content:")
            print(''.join(content))
        
        # Modify the content (e.g., add a prefix to each line)
        modified_content = [f"Modified: {line}" for line in content]
        
        # Attempt to write the modified content to a new file
        with open(output_filename, 'w') as output_file:
            output_file.writelines(modified_content)
            print(f"\nSuccessfully wrote modified content to {output_filename}")
            print("Modified file content:")
            print(''.join(modified_content))
    
    except FileNotFoundError:
        print(f"Error: The file '{input_filename}' does not exist.")
    except PermissionError:
        print(f"Error: You do not have permission to access '{input_filename}'.")
    except IOError as e:
        print(f"Error: An I/O error occurred while processing the file: {e}")
    except Exception as e:
        print(f"An unexpected error occurred: {e}")

# Run the program
process_file()
