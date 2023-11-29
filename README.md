# Task-3-Codsoft-Contact-Book
# Defining new class named ContactBook, within it i'll define different required functions

class ContactBook:
    def __init__(self, name, phone, email, address):
        self.name = name
        self.phone = phone
        self.email = email
        self.address = address

def add_contact():
    name = input("Enter contact name: ")
    phone = input("Enter contact phone number: ")
    email = input("Enter contact email address: ")
    address = input("Enter contact address: ")

    new_contact = ContactBook(name, phone, email, address)
    contacts.append(new_contact)
    print("New Contact added successfully in your Contact Book!")

def view_contact():
    if not contacts:
        print("No contacts found.")
        return

    for contact in contacts:
        print("Name:", contact.name)
        print("Phone:", contact.phone)
        print("Email:", contact.email)
        print("Address:", contact.address)
        print("-----------------------------------------")

def search_contact():
    search_term = input("Enter name or phone number you want to search : ")

    found_contacts = []
    for contact in contacts:
        if search_term.lower() in contact.name.lower() or search_term.lower() in contact.phone.lower():
            found_contacts.append(contact)

    if not found_contacts:
        print("Contact not found in Contact Book.")
        return

    for contact in found_contacts:
        print("Name:", contact.name)
        print("Phone:", contact.phone)
        print("Email:", contact.email)
        print("Address:", contact.address)
        print("-----------------------------")

def update_contact():
    contact_name = input("Enter name of the contact you want to update: ")
    found_contact = None

    for contact in contacts:
        if contact.name.lower() == contact_name.lower():
            found_contact = contact
            break

    if not found_contact:
        print("Contact not found in Contact Book.")
        return

    new_name = input("Enter new name (either press enter to skip): ")
    if new_name:
        found_contact.name = new_name

    new_phone = input("Enter new phone number (either press enter to skip): ")
    if new_phone:
        found_contact.phone = new_phone

    new_email = input("Enter new email address (either press enter to skip): ")
    if new_email:
        found_contact.email = new_email

    new_address = input("Enter new address (either press enter to skip): ")
    if new_address:
        found_contact.address = new_address

    print("Contact Book updated successfully!")

def delete_contact():
    contact_name = input("Enter name of the contact you wish to delete: ")
    found_contact = None

    for contact in contacts:
        if contact.name.lower() == contact_name.lower():
            found_contact = contact
            break

    if not found_contact:
        print("Contact not found in Contact Book.")
        return

    contacts.remove(found_contact)
    print("Contact deleted successfully!")

contacts = []

while True:
    print("----------------------------------------------------------------------------------------------------------")
    print("Welcome to Contact Book Manager")
    print("-------------------------------")
    print("Select an operation you want to perform out of following options in your Contact Book")
    print("1. Add Contact")
    print("2. View Contact Book List")
    print("3. Search Contact Book")
    print("4. Update Contact Book")
    print("5. Delete Contact Book")
    print("6. Exit from program")
    print("-----------------------------------------------------------------------------------------------------------")

    choice = input("Enter your choice: ")

    if choice == '1':
        add_contact()
    elif choice == '2':
        view_contact()
    elif choice == '3':
        search_contact()
    elif choice == '4':
        update_contact()
    elif choice == '5':
        delete_contact()
    elif choice == '6':
        print("Exiting from Contact Book manager, Thank You for using...")
        break
    else:
        print("Invalid choice. Please choose from the available options.")
