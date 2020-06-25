1. List in python with in for loop. [ref](https://stackoverflow.com/questions/11479392/what-does-a-for-loop-within-a-list-do-in-python)

2. Creating lock for process in python on unix based system.
~~~python
def get_exclusive_lock(path,partner):
    """
    Create directory based lock.
    :param path: The directory inside which lock will be created.
    :param partner: The partner corresponds to which creating lock.
    :return:
    """
    try:
        os.makedirs(path)
    except:
        pass

    lock_ac = False
    while not lock_ac:
        try:
            os.mkdir(os.path.join(path,str(partner) ))
            lock_ac = True
            logger.warn("Lock has been acquired for partner %d",partner)
        except:
            logger.error("Lock has already been taken for %d, will wait for 600 sec and retry",partner)
            time.sleep(600)
            continue

def clear_lock(path,partner):
    """
    Clear the existing lock.
    :param path: The directory which contain the lock.
    :param partner: The partner corresponds to which lock need to be removed.
    :return:
    """
    partner_path = os.path.join(path,str(partner) )
    try:
        os.rmdir(partner_path)
        logger.warn("Lock has been cleared for partner %d",partner)
    except:
        logger.warn("fail to clear lock for partner %d",partner)
        if os.path.isdir(partner_path):
            shutil.rmtree(partner_path, ignore_errors = True)
        pass

~~~

