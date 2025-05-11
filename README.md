def modify_content(content):
    """
    Modify the content as needed.
    For demonstration, this function converts the text to uppercase.
    """
    return content.upper()

def main():
    filename = input("Enter the name of the file to read: ")

    try:
        with open(filename, 'r') as file:
            content = file.read()
    except FileNotFoundError:
        print(f"Error: The file '{filename}' was not found.")
        return
    except PermissionError:
        print(f"Error: Permission denied when trying to read '{filename}'.")
        return
    except Exception as e:
        print(f"An unexpected error occurred: {e}")
        return

    modified_content = modify_content(content)
    new_filename = f"modified_{filename}"

    try:
        with open(new_filename, 'w') as new_file:
            new_file.write(modified_content)
        print(f"Modified content has been written to '{new_filename}'.")
    except Exception as e:
        print(f"An error occurred while writing to '{new_filename}': {e}")

if __name__ == "__main__":
    main()
