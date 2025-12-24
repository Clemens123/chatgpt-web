  const latestMessages = get(currentChatMessages); // Get the most up-to-date message list
  if (latestMessages.length > 0) {
    const lastMsg = latestMessages[latestMessages.length - 1];
    // Only update if the last message belongs to a *stored* branch
    const currentChatData = get(chatsStorage).find(c => c.id === chatId);
    const branchesLength = currentChatData?.branches?.length ?? 0;
    if (lastMsg.branchInfo && lastMsg.branchInfo.current > 0 && lastMsg.branchInfo.current <= branchesLength) {
        const branchIndexToUpdate = lastMsg.branchInfo.current - 1; // 0-based index
        // const chats = get(chatsStorage); // Already got currentChatData
        // const currentChatData = chats.find(c => c.id === chatId); // Already got currentChatData

        if (currentChatData && currentChatData.branches && branchIndexToUpdate < currentChatData.branches.length) { // Keep inner check for safety
            // ... rest of block unchanged ...
        }
    }
  } 