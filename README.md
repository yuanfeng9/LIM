max_capacity = 130
brain_list = [
    {"id": "MEMORY-1", "desc": "Graduation Hologram", "size": 45},
    {"id": "MEMORY-2", "desc": "Moon Colony Trip", "size": 50},
    {"id": "MEMORY-3", "desc": "Smoothie Recipe", "size": 5},
    {"id": "MEMORY-4", "desc": "Lost Childhood Toy", "size": 15}
]
cloud_list = []

storage = sum(item["size"] for item in brain_list)
free_storage = max(0, max_capacity - storage)

print("==================================================")
print("           2050 ACTIVE BRAIN STORAGE              ")
print("==================================================")
for memory in brain_list:
    print(f"{memory['id']} | {memory['desc']} | {memory['size']} TB")
print("--------------------------------------------------")
print(f"Memories Occupied Storage : {storage} TB")
print(f"Maximum Brain Capacity    : {max_capacity} TB")
print(f"Remaining Free Storage    : {free_storage} TB")

if storage >= max_capacity:
    print("System Status             : 🚨 MAXIMUM CAPACITY REACHED!!!!")
else:
    print("System Status             : ✅ OPTIMAL STATE")
print("==================================================\n")


# LOOPING MEMORY ADDITION
while True:
    answer = input("Do you want to add a new memory? (Yes / No): ")

    if answer == "Yes":
        desc = input("\nEnter memory description: ")
        size = int(input("Enter size in TB: "))

        new_mem = {"id": "MEM-5", "desc": desc, "size": size}
        brain_list.append(new_mem)
        print(f"\nSaved: '{desc}' added to brain storage!\n")

        storage = storage + size
        free_storage = max_capacity - storage
        if free_storage < 0:
            free_storage = 0


        if storage >= max_capacity:
            print(f"🚨 MEMORY FULL! Usage reached {storage} TB / {max_capacity} TB.")
            move_choice = input("Move memories to cloud to free up space? (Yes / No): ")

            if move_choice == "Yes":
                print("\nTransferring oldest memory to Cloud Storage...")
                removed_item = brain_list.pop(0)
                cloud_list.append(removed_item)
                storage -= removed_item["size"]
                
                print(f"Moved to Cloud: {removed_item['desc']} ({removed_item['size']} TB)")
                print("Congratulations, Transfer Completed !!!!\n")
                break  # Stops looping 
            else:
                print("Storage remains FULL.\n")

    elif answer == "No":
        print("\nStopping process...")
        break

# DISPLAY CLOUD DRIVe
print("\n==================================================")
print("           ☁️ UNLIMITED CLOUD DRIVE               ")
print("==================================================")
if len(cloud_list) == 0:
    print(" (Cloud drive is empty)")
else:
    for item in cloud_list:
        print(f"{item['id']} | {item['desc']} | {item['size']} TB")
print("==================================================")
print("Goodbye!")
ugted
