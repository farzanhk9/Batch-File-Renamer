import os

# Function to rename files in a directory
def rename_files(directory, prefix="", suffix="", new_extension=None):
    # Check if the directory exists
    if not os.path.exists(directory):
        print("The specified directory does not exist.")
        return

    # Get all files in the directory
    files = os.listdir(directory)

    # Loop through each file
    for filename in files:
        # Generate the new name for the file
        new_name = filename

        # Add prefix and suffix to the file name
        if prefix:
            new_name = prefix + new_name
        if suffix:
            name, ext = os.path.splitext(new_name)
            new_name = name + suffix + ext

        # Change the extension if required
        if new_extension:
            name, ext = os.path.splitext(new_name)
            new_name = name + "." + new_extension

        # Construct full file paths
        old_file = os.path.join(directory, filename)
        new_file = os.path.join(directory, new_name)

        # Rename the file
        try:
            os.rename(old_file, new_file)
            print(f"Renamed: {filename} -> {new_name}")
        except Exception as e:
            print(f"Error renaming {filename}: {e}")

# Main program
def main():
    directory = input("Enter the directory path where your files are located: ")
    prefix = input("Enter a prefix to add to all files (leave empty if none): ")
    suffix = input("Enter a suffix to add to all files (leave empty if none): ")
    new_extension = input("Enter a new extension for all files (leave empty to keep the original extension): ")

    # Rename files in the given directory
    rename_files(directory, prefix, suffix, new_extension)

# Run the program
if __name__ == "__main__":
    main()

